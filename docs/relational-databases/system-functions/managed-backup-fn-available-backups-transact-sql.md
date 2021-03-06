---
title: managed_backup. fn_available_backups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.fn_available_backups
- smart_admin.fn_available_backups_TSQL
- fn_available_backups_TSQL
- fn_available_backups
dev_langs:
- TSQL
helpviewer_keywords:
- fn_available_backups
- smart_admin.fn_available_backups
ms.assetid: 7aa84474-16e5-49bd-a703-c8d1408ef107
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c7bb6e33dfd2ee6640e9588011d3686a72a0188
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68140667"
---
# <a name="managed_backupfn_available_backups-transact-sql"></a>managed_backup. fn_available_backups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Restituisce una tabella di 0, una o più righe dei file di backup disponibili per il database specificato. I file di backup restituiti sono backup creati dal [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
managed_backup.fn_available_backups ([@database_name = ] 'database name')  
```  
  
##  <a name="Arguments"></a> Argomenti  
 @database_name  
 Nome del database. È @database_name di tipo nvarchar (512).  
  
## <a name="table-returned"></a>Tabella restituita  
 Alla tabella viene applicato un vincolo cluster univoco (database_guid, backup_start_date e first_lsn, backup_type).   
Se un database viene eliminato e quindi ricreato, vengono restituiti i set di backup per tutti i database. L'output viene ordinato in base a database_guid, che identifica in modo univoco ogni database.   
Se sono presenti gap in LSN significa che è presente un'interruzione nella catena di log; la tabella conterrà una riga speciale per ogni segmento LSN mancante.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|Backup_path|NVARCHAR(260) COLLATE Latin1_General_CI_AS_KS_WS|URL del file di backup.|  
|backup_type|NVARCHAR (6)|' DB ' per il backup del database ' LOG ' per il backup del log|  
|expiration_date|DATETIME|Data in cui si prevede l'eliminazione di questo file. Viene impostata in base alla capacità di recuperare il database fino a un punto nel tempo nel periodo di memorizzazione specificato.|  
|database_guid|UNIQUEIDENTIFIER|Valore GUID per il database specificato.  Il GUID identifica in modo univoco un database.|  
|first_lsn|NUMERIC(25, 0)|Numero di sequenza del file di log del primo record, ovvero del record di log meno recente nel set di backup. Può essere NULL.|  
|last_lsn|NUMERIC(25, 0)|Numero di sequenza del file di log (LSN) del record di log successivo dopo il set di backup. Può essere NULL.|  
|backup_start_date|DATETIME|Data e ora in cui è stata avviata l'operazione di backup.|  
|backup_finish_date|NVARCHAR(128)|Data e ora in cui è terminata l'operazione di backup.|  
|machine_name|NVARCHAR(128)|Nome del computer dove è stata istallata l'istanza di SQL Server ed è in esecuzione il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].|  
|last_recovery_fork_id|UNIQUEIDENTIFIER|Numero di identificazione per il fork di recupero finale.|  
|first_recovery_fork_id|UNIQUEIDENTIFIER|ID del fork di recupero iniziale. Per i backup di dati, first_recovery_fork_guid è uguale a last_recovery_fork_guid.|  
|fork_point_lsn|NUMERIC(25, 0)|Se first_recovery_fork_id è diverso da last_recovery_fork_id, è il numero di sequenza del file di log (LSN) del punto di fork. Negli altri casi il valore è NULL.|  
|availability_group_guid|UNIQUEIDENTIFIER|Se un database è un database di Always On, questo è il GUID del gruppo di disponibilità. Negli altri casi il valore è NULL.|  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 Sono richieste le autorizzazioni **Select** per questa funzione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono elencati tutti i backup disponibili [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] di cui è stato eseguito il backup per il database ' MyDB '  
  
```  
SELECT *   
FROM managed_backup.fn_available_backups ('MyDB')  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server backup gestito Microsoft Azure](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)   
 [Ripristino da backup archiviati in Microsoft Azure](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
