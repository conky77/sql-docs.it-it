---
title: sp_help_agent_default (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_agent_default
- sp_help_agent_default_TSQL
helpviewer_keywords:
- sp_help_agent_default
ms.assetid: 7ba55e39-05dd-43c7-b5da-b268ed8426dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: c0797b8fe4a2ba496b28f0c347eb5349e77e91e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68762756"
---
# <a name="sp_help_agent_default-transact-sql"></a>sp_help_agent_default (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Restituisce l'ID della configurazione predefinita per il tipo di agente passato come parametro. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_agent_default [ @profile_id= ] profile_id OUTPUT   
        , [ @agent_type = ] agent_type  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @profile_id = ] _profile_idOUTPUT`ID della configurazione predefinita per il tipo di agente. *profile_id* è di **tipo int**e non prevede alcun valore predefinito. *profile_id* è anche un parametro di output e restituisce l'ID della configurazione predefinita per il tipo di agente.  
  
`[ @agent_type = ] 'agent_type'`Tipo di agente. *agent_type* è di **tipo int**e non prevede alcun valore predefinito. i possibili valori sono i seguenti.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**1**|Agente snapshot.|  
|**2**|Agente di lettura log.|  
|**3**|Agente di distribuzione.|  
|**4**|Agente di merge.|  
|**9**|Agente di lettura coda|  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_agent_default** viene utilizzato in tutti i tipi di replica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** o del ruolo predefinito del database **replmonitor** possono eseguire **sp_help_agent_default**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
