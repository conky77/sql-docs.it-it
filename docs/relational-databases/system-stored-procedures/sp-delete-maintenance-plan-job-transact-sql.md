---
title: sp_delete_maintenance_plan_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan_job
- sp_delete_maintenance_plan_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_job
ms.assetid: 1c2148c3-2928-4d9b-b1c8-3512cfbd6a63
author: stevestein
ms.author: sstein
ms.openlocfilehash: c67731907d105c6fb2cc48ecf3232d2c9d89c5b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68009197"
---
# <a name="sp_delete_maintenance_plan_job-transact-sql"></a>sp_delete_maintenance_plan_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove l'associazione tra il piano di manutenzione specificato e un processo.  
  
> [!NOTE]  
>  Questa stored procedure viene utilizzata con piani di manutenzione del database. Questa caratteristica è stata sostituita da piani di manutenzione che non utilizzano questa stored procedure. Utilizzare questa stored procedure per mantenere i piani di manutenzione del database nelle installazioni aggiornate da una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_maintenance_plan_job [ @plan_id = ] 'plan_id' ,   
   [ @job_id = ] 'job_id'   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @plan_id = ] 'plan\_id'`Specifica l'ID del piano di manutenzione. *plan_id* è di tipo **uniqueidentifier**e deve essere un ID valido.  
  
`[ @job_id = ] 'job\_id'`Specifica l'ID del processo a cui è associato il piano di manutenzione. *job_id* è di tipo **uniqueidentifier**e deve essere un ID valido.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_delete_maintenance_plan_job** deve essere eseguito dal database **msdb** .  
  
 Quando tutti i processi sono stati rimossi dal piano di manutenzione, è consigliabile che gli utenti eseguano **sp_delete_maintenance_plan_db** per rimuovere dal piano i database rimanenti.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_delete_maintenance_plan_job**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente il processo "B8FCECB1-E22C-11D2-AA64-00C04F688EAE" viene eliminato dal piano di manutenzione.  
  
```  
EXECUTE   sp_delete_maintenance_plan_job N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'B8FCECB1-E22C-11D2-AA64-00C04F688EAE';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Stored procedure del piano di manutenzione del database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
