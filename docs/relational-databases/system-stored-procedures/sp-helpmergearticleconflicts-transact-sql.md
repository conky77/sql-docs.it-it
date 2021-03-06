---
title: sp_helpmergearticleconflicts (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticleconflicts
- sp_helpmergearticleconflicts_TSQL
helpviewer_keywords:
- sp_helpmergearticleconflicts
ms.assetid: 4678a2b9-9a5f-4193-a20d-2e11fc896c3a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85e75e1ce52866eb04b3c410f021db8de392239a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122333"
---
# <a name="sp_helpmergearticleconflicts-transact-sql"></a>sp_helpmergearticleconflicts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce gli articoli della pubblicazione che presentano conflitti. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di sottoscrizione di tipo merge del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpmergearticleconflicts [ [ @publication = ] 'publication' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publsher_db' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publication = ] 'publication'`Nome della pubblicazione di tipo merge. *Publication* è di **%** **tipo sysname**e il valore predefinito è, che restituisce tutti gli articoli del database in cui sono presenti conflitti.  
  
`[ @publisher = ] 'publisher'`Nome del server di pubblicazione. *Publisher* è di **tipo sysname**e il valore predefinito è null.  
  
`[ @publisher_db = ] 'publisher_db'`Nome del database del server di pubblicazione. *publisher_db* è di **tipo sysname**e il valore predefinito è null.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**articolo**|**sysname**|Nome dell'articolo.|  
|**source_owner**|**sysname**|Proprietario dell'oggetto di origine.|  
|**source_object**|**nvarchar (386)**|Nome dell'oggetto di origine.|  
|**conflict_table**|**nvarchar(258)**|Nome della tabella in cui sono archiviati i conflitti di inserimento o aggiornamento.|  
|**guidcolname**|**sysname**|Nome del valore RowGuidCol per l'oggetto di origine.|  
|**centralized_conflicts**|**int**|Indica se i record dei conflitti vengono archiviati nel server di pubblicazione specificato.|  
  
 Se l'articolo include solo conflitti Delete e nessuna riga di **conflict_table** , il nome del **conflict_table** nel set di risultati è null.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpmergearticleconflicts** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** e del ruolo predefinito del database **db_owner** possono eseguire **sp_helpmergearticleconflicts**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
