---
title: sysmail_help_account_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 857e4139081833980ee6c90eca9d90d16d4c0ad2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72305150"
---
# <a name="sysmail_help_account_sp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza un elenco di informazioni (eccetto le password) sugli account di Posta elettronica database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @account_id = ] account_id`ID dell'account per cui elencare le informazioni. *account_id* è di **tipo int**e il valore predefinito è null.  
  
`[ @account_name = ] 'account_name'`Nome dell'account per cui elencare le informazioni. *account_name* è di **tipo sysname**e il valore predefinito è null.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Restituisce un set di risultati contenente le colonne elencate di seguito.  
  
||||  
|-|-|-|  
|Nome colonna|Tipo di dati|Descrizione|  
|**account_id**|**int**|ID dell'account.|  
|**nome**|**sysname**|Nome dell'account.|  
|**Descrizione**|**nvarchar(256)**|Descrizione dell'account.|  
|**email_address**|**nvarchar(128)**|Indirizzo di posta elettronica da cui inviare i messaggi.|  
|**display_name**|**nvarchar(128)**|Nome visualizzato dell'account.|  
|**replyto_address**|**nvarchar(128)**|Indirizzo a cui vengono inviate le risposte ai messaggi da questo account.|  
|**ServerType**|**sysname**|Tipo di server di posta elettronica per l'account.|  
|**nomeserver**|**sysname**|Nome del server di posta elettronica per l'account.|  
|**porta**|**int**|Numero della porta del server di posta elettronica.|  
|**nome utente**|**nvarchar(128)**|Nome utente da utilizzare per accedere al server di posta elettronica se il server di posta elettronica utilizza l'autenticazione. Quando **username** è NULL, posta elettronica database non utilizza l'autenticazione per questo account.|  
|**use_default_credentials**|**bit**|Specifica se inviare la posta elettronica al server SMTP utilizzando le credenziali di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** è di bit e non prevede alcun valore predefinito. Se questo parametro è 1, Posta elettronica database utilizza le credenziali del servizio [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Quando questo parametro è 0, posta elettronica database utilizza il ** \@nome utente** e ** \@la password** per l'autenticazione nel server SMTP. Se ** \@nome utente** e ** \@password** sono null, posta elettronica database usa l'autenticazione anonima. Prima di specificare questo parametro consultare l'amministratore del server SMTP.|  
|**enable_ssl**|**bit**|Specifica l'utilizzo della crittografia mediante SSL (Secure Sockets Layer) da parte di Posta elettronica database. Utilizzare questa opzione se SSL è obbligatorio per il server SMTP. **enable_ssl** è di bit e non prevede alcun valore predefinito. 1 indica che le comunicazioni vengono crittografate mediante SSL. 0 indica che i messaggi vengono inviati senza utilizzare la crittografia SSL.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando non viene specificato alcun *account_id* o *account_name* , **sysmail_help_account** elenca le informazioni su tutti gli account di posta elettronica database nell'istanza di Microsoft SQL Server.  
  
 Il stored procedure **sysmail_help_account_sp** si trova nel database **msdb** ed è di proprietà dello schema **dbo** . La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione per questa procedura vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 **A. Visualizzazione di un elenco di informazioni per tutti gli account**  
  
 Nell'esempio seguente viene visualizzato un elenco di informazioni per tutti gli account nell'istanza.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp ;  
```  
  
 Quello che segue è un set di risultati di esempio, modificato per adattarlo alla lunghezza di riga.  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- --------------------------------------- ------------------------- -------------------------------- --------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
149         Audit Account                Account for audit e-mail.               audit@Adventure-Works.com Automated Mailer (Audit)         NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
```  
  
 **B. Visualizzazione di un elenco di informazioni per un account specifico**  
  
 Nell'esempio seguente viene visualizzato un elenco di informazioni di account per l'account denominato `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
 Quello che segue è un set di risultati di esempio, modificato per adattarlo alla lunghezza di riga.  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- ------------------------------------------------------ ------------------------- ---------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL     0                       0       
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Creazione di un account Posta elettronica database](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Stored procedure di Posta elettronica database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
