---
title: sys. sp_rda_test_connection (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_test_connection
- sys.sp_rda_test_connection_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_test_connection stored procedure
ms.assetid: e2ba050c-d7e3-4f33-8281-c9b525b4edb4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69b3b9eae6c292b9501dfbe74b84d7399304a291
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72305160"
---
# <a name="syssp_rda_test_connection-transact-sql"></a>sys. sp_rda_test_connection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Verifica la connessione da SQL Server al server Azure remoto e segnala problemi che possono impedire la migrazione dei dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EXECUTE sys.sp_rda_test_connection  
   @database_name = N'db_name',   
   @server_address = N'azure_server_fully_qualified_address',  
   @azure_username = N'azure_username',   
   @azure_password = N'azure_password',  
   @credential_name = N'credential_name'  
  
```  
  
## <a name="arguments"></a>Argomenti  
 @database_name= N'*db_name*'  
 Nome del database di SQL Server abilitato per l'estensione. Questo parametro è facoltativo.  
  
 @server_address= N'*azure_server_fully_qualified_address*'  
 Indirizzo completo del server Azure.  
  
-   Se si specifica un valore per ** \@database_name**, ma il database specificato non è abilitato per l'estensione, è necessario specificare un valore per ** \@server_address**.  
  
-   Se si specifica un valore per ** \@database_name**e il database specificato è abilitato per l'estensione, non è necessario specificare un valore per ** \@server_address**. Se si specifica un valore per ** \@server_address**, il stored procedure lo ignora e usa il server di Azure esistente già associato al database abilitato per l'estensione.  
  
 @azure_username= N'*azure_username*  
 Nome utente del server Azure remoto.  
  
 @azure_password= N'*azure_password*'  
 Password per il server Azure remoto.  
  
 @credential_name= N'*credential_name*'  
 Anziché fornire un nome utente e una password, è possibile specificare il nome di una credenziale archiviata nel database abilitato per l'estensione.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 In caso di **esito positivo**, sp_rda_test_connection restituisce l'errore 14855 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_SUCCEEDED) con EX_INFO di gravità e un codice restituito con esito positivo.  
  
 In caso di **errore**, sp_rda_test_connection restituisce l'errore 14856 (STRETCH_MAJOR, STRETCH_CONNECTION_TEST_PROC_FAILED) con EX_USER di gravità e un codice di errore restituito.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|link_state|INT|Uno dei valori seguenti, che corrispondono ai valori per **link_state_desc**.<br /><br /> -0<br />-1<br />-2<br />-3<br />-4|  
|link_state_desc| varchar(32)|Uno dei valori seguenti, che corrispondono ai valori precedenti per **link_state**.<br /><br /> -INTEGRo<br />     Il tra SQL Server e il server Azure remoto è integro.<br />-ERROR_AZURE_FIREWALL<br />     Il firewall di Azure impedisce il collegamento tra SQL Server e il server Azure remoto.<br />-ERROR_NO_CONNECTION<br />     SQL Server non è in grado di effettuare una connessione al server Azure remoto.<br />-ERROR_AUTH_FAILURE<br />     Un errore di autenticazione impedisce il collegamento tra SQL Server e il server Azure remoto.<br />-ERRORE<br />     Un errore che non è un problema di autenticazione, un problema di connettività o un problema del firewall impedisce il collegamento tra SQL Server e il server Azure remoto.|  
|error_number|INT|Il numero dell'errore. Se non si verifica alcun errore, il campo è NULL.|  
|error_message|nvarchar(1024)|Messaggio di errore. Se non si verifica alcun errore, il campo è NULL.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  
  
## <a name="examples"></a>Esempi  
  
### <a name="check-the-connection-from-sql-server-to-the-remote-azure-server"></a>Controllare la connessione dal SQL Server al server Azure remoto  
  
```sql  
EXECUTE sys.sp_rda_test_connection @database_name = N'<Stretch-enabled database>'  
GO  
  
```  
  
 I risultati mostrano che SQL Server non è in grado di connettersi al server Azure remoto.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|2|ERROR_NO_CONNECTION|*\<numero di errore correlato alla connessione>*|*\<messaggio di errore correlato alla connessione>*|  
  
### <a name="check-the-azure-firewall"></a>Controllare il firewall di Azure  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 I risultati mostrano che il firewall di Azure impedisce il collegamento tra SQL Server e il server Azure remoto.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|1|ERROR_AZURE_FIREWALL|*\<numero di errore relativo al firewall>*|*\<messaggio di errore relativo al firewall>*|  
  
### <a name="check-authentication-credentials"></a>Verifica credenziali di autenticazione  
  
```sql  
USE <Stretch-enabled database>  
GO  
EXECUTE sys.sp_rda_test_connection  
GO  
  
```  
  
 I risultati mostrano che un errore di autenticazione impedisce il collegamento tra SQL Server e il server Azure remoto.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|3|ERROR_AUTH_FAILURE|*\<numero di errore correlato all'autenticazione>*|*\<messaggio di errore correlato all'autenticazione>*|  
  
### <a name="check-the-status-of-the-remote-azure-server"></a>Verificare lo stato del server Azure remoto  
  
```sql  
USE <SQL Server database>  
GO  
EXECUTE sys.sp_rda_test_connection   
    @server_address = N'<server name>.database.windows.net',   
    @azure_username = N'<user name>',   
    @azure_password = N'<password>'  
GO  
  
```  
  
 I risultati mostrano che la connessione è integra e che è possibile abilitare Stretch Database per il database specificato.  
  
|link_state|link_state_desc|error_number|error_message|  
|-----------------|-----------------------|-------------------|--------------------|  
|0|HEALTHY|NULL|NULL|  
  
  
