---
title: sp_delete_maintenance_plan_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan_db_TSQL
- sp_delete_maintenance_plan_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_db
- maintenance plans [SQL Server], deleting
- removing maintenance plan
- disassociating maintenance plan
ms.assetid: d1e8afb5-12ee-492b-a770-ba708ed7c8a4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4843eb9de8badced7e446f20a997a530478c2756
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056524"
---
# <a name="sp_delete_maintenance_plan_db-transact-sql"></a>sp_delete_maintenance_plan_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove l'associazione tra il piano di manutenzione specificato e un database.  
  
> [!NOTE]  
>  Questa stored procedure viene utilizzata con piani di manutenzione del database. Questa caratteristica è stata sostituita da piani di manutenzione che non utilizzano questa stored procedure. Utilizzare questa stored procedure per mantenere i piani di manutenzione del database nelle installazioni aggiornate da una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_maintenance_plan_db [ @plan_id = ] 'plan_id' ,   
     [ @db_name = ] 'database_name'   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @plan_id = ] 'plan\_id'`Specifica l'ID del piano di manutenzione. *plan_id* è di tipo **uniqueidentifier**.  
  
`[ @db_name = ] 'database\_name'`Specifica il nome del database da eliminare dal piano di manutenzione. *database_name* è di **tipo sysname**.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_delete_maintenance_plan_db** deve essere eseguito dal database **msdb** .  
  
 Il **sp_delete_maintenance_plan_db** stored procedure rimuove l'associazione tra il piano di manutenzione e il database specificato. non elimina o Elimina definitivamente il database.  
  
 Quando **sp_delete_maintenance_plan_db** rimuove l'ultimo database dal piano di manutenzione, il stored procedure elimina anche il piano di manutenzione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_delete_maintenance_plan_db**.  
  
## <a name="examples"></a>Esempi  
 Elimina il piano di manutenzione nel database **AdventureWorks2012** , aggiunto in precedenza tramite **sp_add_maintenance_plan_db**.  
  
```  
EXECUTE   sp_delete_maintenance_plan_db N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Stored procedure del piano di manutenzione del database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
