---
title: LOGINPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- BadPasswordCount_TSQL
- BadPasswordTime_TSQL
- IsLockedIsMustChange
- PasswordLastSetTime
- LOGINPROPERTY_TSQL
- LockoutTime
- BadPasswordCount
- PasswordHash
- HistoryLengthIsExpired
- LockoutTime_TSQL
- PasswordHash_TSQL
- HistoryLengthIsExpired_TSQL
- PasswordLastSetTime_TSQL
- BadPasswordTime
- IsLockedIsMustChange_TSQL
- LOGINPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- default database
- LOGINPROPERTY function
ms.assetid: b34df777-79b0-49a5-88db-b99998479a5d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7fb31db6e9b438fbab74a8b23462d8c7dc897d46
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68059758"
---
# <a name="loginproperty-transact-sql"></a>LOGINPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle impostazioni relative ai criteri di gestione degli account di accesso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LOGINPROPERTY ( 'login_name' , 'property_name' )  
```  
  
## <a name="arguments"></a>Argomenti  
 *login_name*  
 Nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per cui verrà restituito lo stato delle proprietà di accesso.  
  
 *propertyname*  
 Espressione contenente le informazioni sulle proprietà da restituire per l'account di accesso. *propertyname* può essere uno dei valori seguenti.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**BadPasswordCount**|Restituisce il numero di tentativi consecutivi di accesso con una password non corretta.|  
|**BadPasswordTime**|Restituisce l'ora dell'ultimo tentativo di accesso con password non corretta.|  
|**DaysUntilExpiration**|Restituisce il numero di giorni che mancano alla scadenza della password.|  
|**DefaultDatabase**|Restituisce il database predefinito dell'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archiviato nei metadati oppure **master** se non è specificato alcun database. Restituisce NULL per utenti di cui è stato effettuato il provisioning non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio utenti autenticati di Windows.|  
|**DefaultLanguage**|Restituisce la lingua predefinita dell'account di accesso archiviata nei metadati. Restituisce NULL per gli utenti di cui è stato effettuato il provisioning non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio utenti autenticati di Windows.|  
|**HistoryLength**|Restituisce il numero di password rilevate per l'account di accesso, utilizzando il meccanismo di applicazione dei criteri password. 0 se i criteri password non vengono applicati. La ripresa dell'applicazione dei criteri password verrà riavviata da 1.|  
|**IsExpired**|Indica se l'account di accesso è scaduto.|  
|**IsLocked**|Indica se l'account di accesso è bloccato.|  
|**IsMustChange**|Indica se la password dell'account di accesso deve essere modificata alla connessione successiva.|  
|**LockoutTime**|Restituisce la data di blocco dell'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a causa del superamento del numero consentito di tentativi di accesso non riusciti.|  
|**PasswordHash**|Restituisce l'hash della password.|  
|**PasswordLastSetTime**|Restituisce la data di impostazione della password corrente.|  
|**PasswordHashAlgorithm**|Restituisce l'algoritmo utilizzato per l'hash della password.|  
  
## <a name="returns"></a>Valori di codice restituiti  
 Il tipo di dati dipende dal valore richiesto.  
  
 **IsLocked**, **IsExpired** e **IsMustChange** sono di tipo **int**.  
  
-   1 se l'account di accesso si trova nello stato specificato.  
  
-   0 se l'account di accesso non si trova nello stato specificato.  
  
 **BadPasswordCount** e **HistoryLength** sono di tipo **int**.  
  
 **BadPasswordTime**, **LockoutTime**, **PasswordLastSetTime** sono di tipo **datetime**.  
  
 **PasswordHash** è di tipo **varbinary**.  
  
 NULL se l'account di accesso non è un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valido.  
  
 **DaysUntilExpiration** è di tipo **int**.  
  
-   0 se l'account di accesso è scaduto o se scadrà nel giorno in cui si esegue la query.  
  
-   -1 se i criteri di sicurezza locale in Windows non prevedono mai la scadenza della password.  
  
-   NULL se l'opzione CHECK_POLICY o CHECK_POICY_EXPIRATION è impostata su OFF per un account di accesso o se il sistema operativo non supporta i criteri password.  
  
 **PasswordHashAlgorithm** è di tipo int.  
  
-   0 se hash SQL7.0  
  
-   1 se hash SHA-1  
  
-   2 se hash SHA-2  
  
-   NULL se l'account di accesso non è un account di accesso di SQL Server valido  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione predefinita restituisce informazioni sulle impostazioni relative ai criteri password per un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché i nomi delle proprietà non supportano la distinzione tra maiuscole e minuscole, **BadPasswordCount** e **badpasswordcount** sono equivalenti. I valori delle proprietà **PasswordHash, PasswordHashAlgorithm** e **PasswordLastSetTime** sono disponibili in tutte le configurazioni supportate di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mentre le altre proprietà sono disponibili solo se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] e se sono abilitate entrambe le opzioni CHECK_POLICY e CHECK_EXPIRATION. Per ulteriori informazioni, vedere [Password Policy](../../relational-databases/security/password-policy.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW per l'account di accesso. Se si richiede l'hash della password, è inoltre richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-checking-whether-a-login-must-change-its-password"></a>R. Verifica della necessità di modificare la password di un account di accesso  
 Nell'esempio seguente viene controllato se la password dell'account di accesso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di `John3` deve essere modificata alla connessione successiva a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT LOGINPROPERTY('John3', 'IsMustChange');  
GO  
```  
  
### <a name="b-checking-whether-a-login-is-locked-out"></a>B. Controllo dell'eventuale blocco di un account di accesso  
 Nell'esempio seguente viene controllato se l'account di accesso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di `John3` è bloccato.  
  
```  
SELECT LOGINPROPERTY('John3', 'IsLocked');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
  
