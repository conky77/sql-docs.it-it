---
title: sp_helppeerrequests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5b9e2a370c9acc9c22dac7e5e60ceb10e08e46ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68137626"
---
# <a name="sp_helppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni su tutte le richieste di stato ricevute dai partecipanti in una topologia di replica peer-to-peer, in cui tali richieste sono state avviate eseguendo [sp_requestpeerresponse &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) in qualsiasi database pubblicato nella topologia. Questa stored procedure viene eseguita nel database di pubblicazione di un server di pubblicazione che partecipa a una topologia di replica peer-to-peer. Per altre informazioni, vedere [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publication = ] 'publication'`Nome della pubblicazione in una topologia peer-to-peer per cui sono state inviate le richieste di stato. *Publication* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @description = ] 'description'`Valore che può essere utilizzato per identificare le singole richieste di stato, che consente di filtrare le risposte restituite in base alle informazioni definite dall'utente fornite durante la chiamata di [sp_requestpeerresponse &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md). *Description* è di **%** **tipo nvarchar (4000)** e il valore predefinito è. Per impostazione predefinita, tutte le richieste dello stato per la pubblicazione vengono restituite. Questo parametro viene utilizzato per restituire solo le richieste di stato con una descrizione che corrisponde al valore fornito nella *Descrizione*, in cui le stringhe di caratteri vengono confrontate utilizzando una clausola [like &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md) .  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**ID**|**int**|Identifica una richiesta.|  
|**pubblicazione**|**sysname**|Nome della pubblicazione per cui è stata inviata la richiesta dello stato.|  
|**sent_date**|**datetime**|Data e ora dell'invio della richiesta dello stato.|  
|**Descrizione**|**nvarchar(4000)**|Informazioni definite dall'utente che possono essere utilizzate per identificare richieste dello stato individuali.|  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helppeerrequests** viene utilizzata nella replica transazionale peer-to-peer.  
  
 **sp_helppeerrequests** viene utilizzato per il ripristino di un database pubblicato in una topologia peer-to-peer.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** o del ruolo predefinito del database **db_owner** possono eseguire **sp_helppeerrequests**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_deletepeerrequesthistory &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
