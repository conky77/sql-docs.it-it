---
title: sp_dropextendedproc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproc
- sp_dropextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproc
ms.assetid: dd93af2c-1b7d-4e39-af23-2d21d270a381
author: stevestein
ms.author: sstein
ms.openlocfilehash: b12ebcfb662db9740efdf918f0857b94144e0ceb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68054302"
---
# <a name="sp_dropextendedproc-transact-sql"></a>sp_dropextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina una stored procedure estesa.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Usare invece l' [integrazione con CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_dropextendedproc [ @functname = ] 'procedure'   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @functname = ] 'procedure'`Nome del stored procedure esteso da eliminare. la *routine* è di **tipo nvarchar (517)** e non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuno  
  
## <a name="remarks"></a>Osservazioni  
 L'esecuzione di **sp_dropextendedproc** Elimina il nome del stored procedure esteso definito dall'utente dalla vista del catalogo [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) e rimuove la voce dalla vista del catalogo [sys. extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) . Questa stored procedure può essere eseguita solo nel database **Master** .  
  
**sp_dropextendedproc** non elimina le stored procedure estese di sistema. L'amministratore di sistema deve invece negare l'autorizzazione EXECUTE per il stored procedure esteso al ruolo **public** .  
  
 Impossibile eseguire **sp_dropextendedproc** all'interno di una transazione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_dropextendedproc**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminata la stored procedure estesa `xp_hello`.  
  
> [!NOTE]  
>  Se questa stored procedure estesa non esiste, viene visualizzato un messaggio di errore.  
  
```  
USE master;  
GO  
EXEC sp_dropextendedproc 'xp_hello';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addextendedproc &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
