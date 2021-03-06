---
title: Connessione loopback di SQL Server
description: Informazioni su come usare una connessione loopback per riconnettersi a SQL Server tramite ODBC per leggere o scrivere dati da uno script Python o R eseguito da sp_execute_external_script. Questo approccio è utile quando non è possibile usare gli argomenti InputDataSet e OutputDataSet di sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2019
ms.topic: conceptual
author: Aniruddh25
ms.author: anmunde
ms.reviewer: dphansen
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c7fa36db48a7912951f0232136945798caf6f7f7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727595"
---
# <a name="loopback-connection-to-sql-server-from-a-python-or-r-script"></a>Connessione loopback a SQL Server da uno script Python o R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Informazioni su come usare una connessione loopback per riconnettersi a SQL Server tramite [ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md) per leggere o scrivere dati da uno script Python o R eseguito da `sp_execute_external_script`sp_execute_external_script. Questo approccio è utile quando non è possibile usare gli argomenti **InputDataSet** e **OutputDataSet** di `sp_execute_external_script`.

## <a name="connection-string"></a>Stringa di connessione

Per eseguire una connessione loopback, è necessario usare una stringa di connessione corretta. Gli argomenti obbligatori comuni sono il nome del [driver ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md), l'indirizzo del server e il nome del database.

### <a name="connection-string-on-windows"></a>Stringa di connessione in Windows

Per l'autenticazione in SQL Server in Windows, lo script Python o R può usare l'attributo della stringa di connessione **Trusted_Connection** per eseguire l'autenticazione con lo stesso utente che ha eseguito sp_execute_external_script.

Ecco un esempio della stringa di connessione loopback in Windows:

``` 
"Driver=SQL Server;Server=.;Database=nameOfDatabase;Trusted_Connection=Yes;"
```

### <a name="connection-string-on-linux"></a>Stringa di connessione in Linux

Per l'autenticazione in SQL Server in Linux, lo script Python o R deve usare gli attributi **ClientCertificate** e **ClientKey** del driver ODBC per eseguire l'autenticazione con lo stesso utente che ha eseguito `sp_execute_external_script`. Questa operazione richiede l'uso del [driver ODBC più recente](../../connect/odbc/download-odbc-driver-for-sql-server.md), ovvero la versione 17.4.1.1.

Ecco un esempio della stringa di connessione loopback in Linux:

```
"Driver=ODBC Driver 17 for SQL Server;Server=fe80::8012:3df5:0:5db1%eth0;Database=nameOfDatabase;ClientCertificate=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitecert.pem;ClientKey=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitekey.pem;TrustServerCertificate=Yes;Trusted_Connection=no;Encrypt=Yes"
```

L'indirizzo del server, il percorso del file del certificato client e il percorso del file di chiave client sono univoci per ogni `sp_execute_external_script` e possono essere ottenuti usando l'API **rx_get_sql_loopback_connection_string()** per Python o **rxGetSqlLoopbackConnectionString()** per R.

Per altre informazioni sugli attributi della stringa di connessione, vedere [Parole chiave e attributi per la stringa di connessione e DSN](https://docs.microsoft.com/sql/connect/odbc/dsn-connection-string-attribute?view=sql-server-linux-ver15#new-connection-string-keywords-and-connection-attributes) per Microsoft ODBC Driver for SQL Server.

## <a name="generate-connection-string-with-revoscalepy-for-python"></a>Generare la stringa di connessione con revoscalepy per Python

È possibile usare l'API **rx_get_sql_loopback_connection_string()** in [revoscalepy](../python/ref-py-revoscalepy.md) per generare una stringa di connessione corretta per una connessione loopback in uno script Python.

Sono accettati gli argomenti seguenti:

| Argomento | Descrizione |
|-|-|
| name_of_database | Nome del database al quale deve essere eseguita la connessione |
| odbc_driver | Nome del driver ODBC |

### <a name="examples"></a>Esempi

Esempio per SQL Server in Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="SQL Server", name_of_database="DBName")
print("Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Esempio per SQL Server in Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="ODBC Driver 17 for SQL Server",
                                                                   name_of_database="DBName")
print("Loopback Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="generate-connection-string-with-revoscaler-for-r"></a>Generare la stringa di connessione con RevoScaleR per R

È possibile usare l'API **rxGetSqlLoopbackConnectionString()** in [RevoScaleR](../r/ref-r-revoscaler.md) per generare una stringa di connessione corretta per una connessione loopback in uno script R.

Sono accettati gli argomenti seguenti:

| Argomento | Descrizione |
|-|-|
| nameOfDatabase | Nome del database al quale deve essere eseguita la connessione |
| odbcDriver | Nome del driver ODBC |

### <a name="examples"></a>Esempi

Esempio per SQL Server in Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <- rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", odbcDriver ="SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName",
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Esempio per SQL Server in Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <-  rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", 
                                                                  odbcDriver ="ODBC Driver 17 for SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName", 
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="next-steps"></a>Passaggi successivi

+ [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)
+ [revoscalepy](../python/ref-py-revoscalepy.md)
+ [RevoScaleR](../r/ref-r-revoscaler.md)
