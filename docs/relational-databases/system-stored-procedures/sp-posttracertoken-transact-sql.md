---
title: sp_posttracertoken (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- posttracerttoken
- posttracerttoken_TSQL
- sp_posttracertoken
- sp_posttracertoken_TSQL
helpviewer_keywords:
- sp_posttracertoken
ms.assetid: 24da5cd2-1c45-475e-93db-5bdf660f1c2c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7629c25264f0b45d68e29e947b1d5c40d02707e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72041178"
---
# <a name="sp_posttracertoken-transact-sql"></a>sp_posttracertoken (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa procedura consente di inserire un token di traccia nel log delle transazioni nel server di pubblicazione e di avviare il processo di traccia delle statistiche di latenza. Le informazioni vengono registrate quando il token di traccia viene scritto nel log delle transazioni, quando viene prelevato dall'agente di lettura log e quando viene applicato dall'agente di distribuzione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione. Per altre informazioni, vedere [Misurazione della latenza e convalida delle connessioni per la replica transazionale](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_posttracertoken [ @publication = ] 'publication'   
    [ , [ @tracer_token_id = ] tracer_token_id OUTPUT  
    [ , [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publication = ] 'publication'`Nome della pubblicazione per cui viene misurata la latenza. *Publication* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @tracer_token_id = ] _tracer_token_id OUTPUT`ID del token di traccia inserito. *tracer_token_id* è di **tipo int** e il valore predefinito è null. si tratta di un parametro di output. Questo valore può essere utilizzato per eseguire [sp_helptracertokenhistory &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md) o [sp_deletetracertokenhistory &#40;Transact-SQL](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)&#41;senza prima eseguire SP_HELPTRACERTOKENS &#40;[Transact-SQL ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md)&#41;.  
  
`[ @publisher = ] 'publisher'`Specifica un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione non. *Publisher* è di **tipo sysname**e il valore predefinito è null. non deve essere specificato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per un server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_posttracertoken** viene utilizzata nella replica transazionale.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-posttracertoken-trans_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** o del ruolo predefinito del database **db_owner** possono eseguire **sp_posttracertoken**.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurare la latenza e convalidare le connessioni per la replica transazionale](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
