---
title: sp_setsubscriptionxactseqno (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setsubscriptionxactseqno
- sp_setsubscriptionxactseqno_TSQL
helpviewer_keywords:
- sp_setsubscriptionxactseqno
ms.assetid: cdb4e0ba-5370-4905-b03f-0b0c6f080ca6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 27a7f35a915e2bff62932124aef64984a63cbd0e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68021079"
---
# <a name="sp_setsubscriptionxactseqno-transact-sql"></a>sp_setsubscriptionxactseqno (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilizzato durante la risoluzione dei problemi per specificare l'ultima transazione recapitata utilizzando il numero di sequenza del file di log (LSN), consentendo all'agente di distribuzione di iniziare a recapitare alla transazione successiva. Al riavvio, il agente di distribuzione restituisce transazioni maggiori di questo limite (LSN) dalla cache del database di distribuzione (msrepl_commands). Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore. e non è supportata per Sottoscrittori non SQL Server.  
  
> [!CAUTION]  
>  Se si utilizza questa stored procedure in modo non corretto oppure si specifica un valore LSN non corretto, è possibile che l'agente di distribuzione annulli modifiche già applicate nel Sottoscrittore oppure ignori tutte le restanti modifiche.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_setsubscriptionxactseqno [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @xact_seqno = ] xact_seqno   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publisher = ] 'publisher'`Nome del server di pubblicazione. *Publisher* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @publisher_db = ] 'publisher_db'`Nome del database di pubblicazione. *publisher_db* è di **tipo sysname**e non prevede alcun valore predefinito. Per un server di pubblicazione non SQL Server, *publisher_db* è il nome del database di distribuzione.  
  
`[ @publication = ] 'publication'`Nome della pubblicazione. *Publication* è di **tipo sysname**e non prevede alcun valore predefinito. Quando la agente di distribuzione è condivisa da più di una pubblicazione, è necessario specificare il valore ALL per *Publication*.  
  
`[ @xact_seqno = ] xact_seqno`LSN della successiva transazione del server di distribuzione da applicare nel Sottoscrittore. *xact_seqno* è di tipo **varbinary (16)** e non prevede alcun valore predefinito.  
  
## <a name="result-set"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**ORIGINAL XACT_SEQNO**|**varbinary (16)**|LSN originale della successiva transazione da applicare nel Sottoscrittore.|  
|**UPDATED XACT_SEQNO**|**varbinary (16)**|LSN aggiornato della successiva transazione da applicare nel Sottoscrittore.|  
|**SUBSCRIPTION STREAM COUNT**|**int**|Numero di flussi di sottoscrizione utilizzati durante l'ultima sincronizzazione.|  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_setsubscriptionxactseqno** viene utilizzata nella replica transazionale.  
  
 Impossibile utilizzare **sp_setsubscriptionxactseqno** in una topologia di replica transazionale peer-to-peer.  
  
 **sp_setsubscriptionxactseqno** può essere utilizzato per ignorare una transazione specifica che causa un errore quando si applica nel Sottoscrittore. Quando si verifica un errore e dopo l'arresto del agente di distribuzione, chiamare [sp_helpsubscriptionerrors &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriptionerrors-transact-sql.md) nel server di distribuzione per recuperare il valore xact_seqno della transazione non riuscita, quindi chiamare **sp_setsubscriptionxactseqno**, passando questo valore per *xact_seqno*. In questo modo verranno elaborati solo i comandi successivi a questo LSN.  
  
 Specificare il valore **0** per *xact_seqno* per recapitare al Sottoscrittore tutti i comandi in sospeso nel database di distribuzione.  
  
 **sp_setsubscriptionxactseqno** possono avere esito negativo se il agente di distribuzione utilizza flussi a più sottoscrizioni.  
  
 Quando si verifica questo errore, è necessario eseguire l'agente di distribuzione con un flusso di sottoscrizione singolo. Per altre informazioni, vedere [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** o del ruolo predefinito del database **db_owner** possono eseguire **sp_setsubscriptionxactseqno**.  
  
## <a name="see-more"></a>Altre informazioni

[Blog: come ignorare una transazione](https://repltalk.com/2019/05/28/how-to-skip-a-transaction/)  
