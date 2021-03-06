---
title: CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATABASE SCOPED CREDENTIAL
- DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_TSQL
- CREATE_DATABASE_SCOPED_CREDENTIAL
- CREATE_DATABASE_SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL_TSQL
- SCOPED_CREDENTIAL
helpviewer_keywords:
- DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], DATABASE SCOPED CREDENTIAL statement
ms.assetid: fe830577-11ca-44e5-953b-2d589d54d045
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=aps-pdw-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f6c4cbb43048e9dff683b510d958e3e25d87e823
ms.sourcegitcommit: 87b932dc4b603a35a19f16e2c681b6a8d4df1fec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77507504"
---
# <a name="create-database-scoped-credential-transact-sql"></a>CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Crea credenziali del database. Le credenziali del database non sono mappata a un account di accesso al server o a un utente di database. Le credenziali vengono usate dal database per accedere al percorso esterno ogni volta che l'operazione eseguita dal database lo richiede.

![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Sintassi

``` 
CREATE DATABASE SCOPED CREDENTIAL credential_name
WITH IDENTITY = 'identity_name'
    [ , SECRET = 'secret' ]

```

## <a name="arguments"></a>Argomenti

*credential_name* specifica il nome della credenziale con ambito database che si vuole creare. *credential_name* non può iniziare con il simbolo del cancelletto (#). perché tale simbolo viene utilizzato per le credenziali di sistema.

IDENTITY **='** _identity\_name_ **'** specifica il nome dell'account da usare per la connessione all'esterno del server. Per importare un file dall'archiviazione BLOB di Azure usando una chiave di condivisione, il nome dell'identità deve essere `SHARED ACCESS SIGNATURE`. Per caricare dati in SQL DW è possibile usare qualsiasi valore valido per l'identità. Per altre informazioni sulle firme di accesso condiviso, vedere [Uso delle firme di accesso condiviso](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).

SECRET **='** _secret_ **'** specifica il segreto richiesto per l'autenticazione in uscita. È necessario specificare `SECRET` per importare un file dall'archiviazione BLOB di Azure. Per caricare dati dall'archiviazione BLOB di Azure in SQL Data Warehouse, il segreto deve essere la chiave di archiviazione di Azure.
> [!WARNING]
> Il valore della chiave di firma di accesso condiviso può iniziare con "?" (punto interrogativo). Quando si usa la chiave di firma di accesso condiviso, è necessario rimuovere il carattere "?" iniziale, altrimenti potrebbe verificarsi un blocco.

## <a name="remarks"></a>Osservazioni

Una credenziale con ambito database è un record contenente le informazioni di autenticazione necessarie per connettersi a una risorsa all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La maggior parte delle credenziali include un utente e una password di Windows.

Prima di creare credenziali con ambito database, il database deve avere una chiave master per proteggere le credenziali. Per altre informazioni, vedere [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md).

Se IDENTITY è un utente di Windows, il segreto può essere la password. Il segreto viene crittografato con la chiave master del servizio. Se la chiave master del servizio viene rigenerata, il segreto viene ricrittografato con la nuova chiave master del servizio.

Altre informazioni sulle credenziali con ambito database sono disponibili nella vista del catalogo [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).

Di seguito sono elencate alcune applicazioni delle credenziali con ambito database:

- [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] usa una credenziale con ambito database per accedere con PolyBase all'archiviazione BLOB di Azure non pubblica o ai cluster Hadoop protetti con Kerberos. Per altre informazioni, vedere [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).

- [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] usa una credenziale con ambito database per accedere con PolyBase all'archiviazione BLOB di Azure non pubblica. Per altre informazioni, vedere [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md).

- [!INCLUDE[ssSDS](../../includes/sssds-md.md)] usa le credenziali con ambito database per la funzionalità di query globale del database. Si tratta della possibilità di eseguire query tra più partizioni di database.

- [!INCLUDE[ssSDS](../../includes/sssds-md.md)] usa le credenziali con ambito database per scrivere file di eventi estesi nell'archiviazione BLOB di Azure.

- [!INCLUDE[ssSDS](../../includes/sssds-md.md)] usa le credenziali con ambito database per i pool di database elastici. Per altre informazioni, vedere [I pool di database elastici consentono di gestire e ridimensionare più database SQL](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)

- [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) e [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md) usano le credenziali con ambito database per accedere ai dati dall'archiviazione BLOB di Azure. Per altre informazioni, vedere [Esempi di accesso bulk ai dati nell'archiviazione BLOB di Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md). 

## <a name="permissions"></a>Autorizzazioni

È richiesta l'autorizzazione **CONTROL** per il database.

## <a name="examples"></a>Esempi

### <a name="a-creating-a-database-scoped-credential-for-your-application"></a>R. Creazione di credenziali con ambito database per l'applicazione

Nell'esempio seguente viene creata la credenziale con ambito database denominata `AppCred`. La credenziale con ambito database include l'utente Windows `Mary5` e una password.

```sql
-- Create a db master key if one does not already exist, using your own password.
CREATE MASTER KEY ENCRYPTION BY PASSWORD='<EnterStrongPasswordHere>';

-- Create a database scoped credential.
CREATE DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'Mary5',
    SECRET = '<EnterStrongPasswordHere>';
```

### <a name="b-creating-a-database-scoped-credential-for-a-shared-access-signature"></a>B. Creazione di credenziali con ambito database per una firma di accesso condiviso

Nell'esempio seguente viene creata una credenziale con ambito database che può essere usata per creare un'[origine dati esterna](../../t-sql/statements/create-external-data-source-transact-sql.md) che può eseguire operazioni in blocco, come ad esempio [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) e [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md). Le firme di accesso condiviso non possono essere usate con PolyBase in SQL Server, nella piattaforma di strumenti analitici o in SQL DW.

```sql
-- Create a db master key if one does not already exist, using your own password.
CREATE MASTER KEY ENCRYPTION BY PASSWORD='<EnterStrongPasswordHere>';

-- Create a database scoped credential.
CREATE DATABASE SCOPED CREDENTIAL MyCredentials
WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
SECRET = 'QLYMgmSXMklt%2FI1U6DcVrQixnlU5Sgbtk1qDRakUBGs%3D';
```

### <a name="c-creating-a-database-scoped-credential-for-polybase-connectivity-to-azure-data-lake-store"></a>C. Creazione di credenziali con ambito database per la connettività di PolyBase ad Azure Data Lake Store

Nell'esempio seguente viene creata una credenziale con ambito database che può essere usata per creare un'[origine dati esterna](../../t-sql/statements/create-external-data-source-transact-sql.md) che può essere usata da PolyBase in Azure SQL Data Warehouse.

Azure Data Lake Store usa un'applicazione di Azure Active Directory per l'autenticazione Service to Service.
[Creare un'applicazione AAD](https://docs.microsoft.com/azure/data-lake-store/data-lake-store-authenticate-using-active-directory) e documentare client_id, OAuth_2.0_Token_EndPoint e chiave prima di creare una credenziale con ambito database.

```sql
-- Create a db master key if one does not already exist, using your own password.
CREATE MASTER KEY ENCRYPTION BY PASSWORD='<EnterStrongPasswordHere>';

-- Create a database scoped credential.
CREATE DATABASE SCOPED CREDENTIAL ADL_User
WITH
    IDENTITY = '<client_id>@\<OAuth_2.0_Token_EndPoint>',
    SECRET = '<key>'
;
```

## <a name="more-information"></a>Ulteriori informazioni

- [Credenziali &#40;motore di database&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)
- [ALTER DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)
- [DROP DATABASE SCOPED CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)
- [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)
- [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)
- [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
