---
title: sp_syscollector_stop_collection_set (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_stop_collection_set_TSQL
- sp_syscollector_stop_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_stop_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 4668cfb7-462f-40d0-948c-8f740a792a4d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3e09efe938dabb031e1c57020f051cd5ab03e55a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68010576"
---
# <a name="sp_syscollector_stop_collection_set-transact-sql"></a>sp_syscollector_stop_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Arresta un set di raccolta.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syscollector_stop_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @stop_collection_job = ] stop_collection_job ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @collection_set_id = ] *collection_set_id*  
 Identificatore univoco locale del set di raccolta. *collection_set_id* è di **tipo int** e il valore predefinito è null. *collection_set_id* deve avere un valore se il *nome* è null.  
  
 [ @name = ] '*Name*'  
 Nome del set di raccolta. *Name* è di **tipo sysname** e il valore predefinito è null. Se *collection_set_id* è null, il *nome* deve avere un valore.  
  
 [ @stop_collection_job = ] *stop_collection_job*  
 Specifica che il processo di raccolta relativo al set di raccolta deve essere arrestato se è in esecuzione. *stop_collection_job* è di **bit** e il valore predefinito è 1.  
  
 *stop_collection_job* si applica solo ai set di raccolta con la modalità di raccolta impostata su memorizzato nella cache. Per ulteriori informazioni, vedere [sp_syscollector_create_collection_set &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 È necessario eseguire sp_syscollector_create_collection_set nel contesto del database di sistema msdb.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa procedura, è necessaria l'appartenenza al ruolo predefinito del database dc_operator (con autorizzazione EXECUTE).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene arrestato un set di raccolta utilizzando il relativo identificatore.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
