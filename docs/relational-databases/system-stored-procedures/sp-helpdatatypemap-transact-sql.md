---
title: sp_helpdatatypemap (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdatatypemap
- sp_helpdatatypemap_TSQL
helpviewer_keywords:
- sp_helpdatatypemap
ms.assetid: 800c9c65-723e-4961-a63d-327987f129f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0b9666c13a2e4d8183d19fade64bf49b13377b9a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771058"
---
# <a name="sp_helpdatatypemap-transact-sql"></a>sp_helpdatatypemap (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Restituisce informazioni sui mapping dei tipi di dati definiti tra [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i sistemi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di gestione non di database (DBMS). Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdatatypemap [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @defaults_only = ] defaults_only ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @source_dbms = ] 'source_dbms'`Nome del sistema DBMS da cui viene eseguito il mapping dei tipi di dati. *source_dbms* è di **tipo sysname**. i possibili valori sono i seguenti.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**MSSQLSERVER**|L'origine è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|L'origine è un database Oracle.|  
  
`[ @source_version = ] 'source_version'`È la versione del prodotto del sistema DBMS di origine. *source_version*è di tipo **varchar (10)** e, se non è specificato, vengono restituiti i mapping dei tipi di dati per tutte le versioni del sistema DBMS di origine. Consente al set dei risultati di venire filtrato in base alla versione di origine del sistema DBMS.  
  
`[ @source_type = ] 'source_type'`Tipo di dati elencato nel sistema DBMS di origine. *source_type* è di **tipo sysname**. se non viene specificato, vengono restituiti i mapping per tutti i tipi di dati nel sistema DBMS di origine. Consente al set di risultati di venire filtrato in base al tipo di dati nel sistema DBMS di origine.  
  
`[ @destination_dbms = ] 'destination_dbms'`Nome del sistema DBMS di destinazione. *destination_dbms* è di **tipo sysname**. i possibili valori sono i seguenti.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**MSSQLSERVER**|La destinazione è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|La destinazione è un database Oracle.|  
|**DB2**|La destinazione è un database IBM DB2.|  
|**SYBASE**|La destinazione è un database Sybase.|  
  
`[ @destination_version = ] 'destination_version'`È la versione del prodotto del sistema DBMS di destinazione. *destination_version*è di tipo **varchar (10)** e, se non è specificato, vengono restituiti i mapping per tutte le versioni del sistema DBMS di destinazione. Consente al set dei risultati di venire filtrato in base alla versione di destinazione del sistema DBMS.  
  
`[ @destination_type = ] 'destination_type'`Tipo di dati elencato nel sistema DBMS di destinazione. *destination_type*è di **tipo sysname**. se non viene specificato, vengono restituiti i mapping per tutti i tipi di dati nel sistema DBMS di destinazione. Consente al set di risultati di venire filtrato in base al tipo di dati nel sistema DBMS di destinazione.  
  
`[ @defaults_only = ] defaults_only`Indica se vengono restituiti solo i mapping dei tipi di dati predefiniti. *defaults_only* è di **bit**e il valore predefinito è **0**. **1** indica che vengono restituiti solo i mapping dei tipi di dati predefiniti. **0** indica che vengono restituiti i mapping predefiniti e i mapping dei tipi di dati definiti dall'utente.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|**mapping_id**|Identifica il mapping dei tipi di dati.|  
|**source_dbms**|Nome e numero di versione del sistema DBMS di origine.|  
|**source_type**|Tipo di dati nel sistema DBMS di origine.|  
|**destination_dbms**|Nome del sistema DBMS di destinazione.|  
|**destination_type**|Tipo di dati nel sistema DBMS di destinazione.|  
|**is_default**|Indica il mapping predefinito o un mapping alternativo. Il valore **0** indica che il mapping è definito dall'utente.|  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpdatatypemap** definisce i mapping dei tipi di dati da autori non SQL Server e da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autori a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sottoscrittori non.  
  
 Quando la combinazione specificata di DBMS di origine e di destinazione non è supportata, **sp_helpdatatypemap** restituisce un set di risultati vuoto.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** nel server di distribuzione o i membri del ruolo predefinito del database **db_owner** nel database di distribuzione possono eseguire **sp_helpdatatypemap**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_getdefaultdatatypemapping &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)  
  
  
