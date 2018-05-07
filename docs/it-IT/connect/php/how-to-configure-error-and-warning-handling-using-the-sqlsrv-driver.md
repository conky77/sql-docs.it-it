---
title: Configurazione errori e degli avvisi usando il Driver SQLSRV | Documenti Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- errors and warnings
ms.assetid: 257c6f53-9137-4619-a613-eee33d2077e8
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42efff9877553fdd478b4acce0e9e71816a00260
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-error-and-warning-handling-using-the-sqlsrv-driver"></a>Procedura: Configurare la gestione degli errori e degli avvisi usando il driver SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo argomento viene descritto come configurare il driver SQLSRV per la gestione degli errori e degli avvisi.  
  
Per impostazione predefinita, il driver SQLSRV considera gli avvisi come errori. una chiamata a un **sqlsrv** funzione che genera un errore o un avviso restituisce **false**. Per disabilitare questo comportamento, utilizzare il [sqlsrv_configure](../../connect/php/sqlsrv-configure.md) (funzione). Quando la riga di codice seguente è inclusa all'inizio di uno script, un **sqlsrv** funzione che genera solo avvisi, ovvero senza errori, non verrà restituito **false**:  
  
`sqlsrv_configure("WarningsReturnAsErrors", 0);`  
  
La riga di codice seguente Reimposta il comportamento predefinito (gli avvisi vengono considerati come errori):  
  
`sqlsrv_configure("WarningsReturnAsErrors", 1);`  
  
> [!NOTE]  
> Gli avvisi che corrispondono ai valori SQLSTATE 01000, 01001, 01003 e 01S02 non vengono mai considerati come errori. Indipendentemente dalla configurazione, una funzione **sqlsrv** che genera solo gli avvisi che corrispondono a uno di questi stati non restituisce **false**.  
  
Il valore di **WarningsReturnAsErrors** può essere impostato anche nel file php.ini. Ad esempio, questa voce nella `[sqlsrv]` sezione del file PHP. ini consente di disattivare il comportamento predefinito.  
  
`sqlsrv.WarningsReturnAsErrors = 0`  
  
Per informazioni sul recupero delle informazioni su errori e avvisi, vedere [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) e [Procedura: Gestire errori e avvisi](../../connect/php/how-to-handle-errors-and-warnings-using-the-sqlsrv-driver.md).  
  
## <a name="example"></a>Esempio  
L'esempio di codice riportato di seguito descrive come disabilitare il comportamento di gestione degli errori predefinito. L'esempio usa il comando PRINT Transact-SQL  per generare un avviso. Per ulteriori informazioni sul comando PRINT, vedere [PRINT (Transact-SQL)](../../t-sql/language-elements/print-transact-sql.md).  
  
Nell'esempio viene innanzitutto illustrato il comportamento di gestione degli errori predefinito eseguendo una query che genera un avviso. L'avviso viene considerato come errore. Dopo aver modificato la configurazione di gestione degli errori, viene eseguita la stessa query. L'avviso non viene considerato come errore.  
  
Nell'esempio si presuppone che SQL Server sia installato nel computer locale. Quando si esegue l'esempio dalla riga di comando, tutto l'output viene scritto nel browser.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName );  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* The Transact-SQL PRINT statement can be used to return   
informational or warning messages*/  
$tsql = "PRINT 'The PRINT statement can be used ";  
$tsql .= "to return user-defined warnings.'";  
  
/* Execute the query and print any errors. */  
$stmt1 = sqlsrv_query( $conn, $tsql);  
if($stmt1 === false)  
{  
     echo "By default, warnings are treated as errors:\n";  
     /* Dump errors in the error collection. */  
     print_r(sqlsrv_errors(SQLSRV_ERR_ERRORS));  
}  
  
/* Disable warnings as errors behavior. */  
sqlsrv_configure("WarningsReturnAsErrors", 0);  
  
/* Execute the same query and print any errors. */  
$stmt2 = sqlsrv_query( $conn, $tsql);  
if($stmt2 === false)  
{  
     /* Dump errors in the error collection. */  
     /* Since the warning generated by the query is be treated as   
        an error, this block of code will not be executed. */  
     print_r(sqlsrv_errors(SQLSRV_ERR_ERRORS));  
}  
else  
{  
     echo "After calling ";  
     echo "sqlsrv_configure('WarningsReturnAsErrors', 0), ";  
     echo "warnings are not treated as errors.";  
}  
  
/*Close the connection. */  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Attività di registrazione](../../connect/php/logging-activity.md)

[Guida di programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
  