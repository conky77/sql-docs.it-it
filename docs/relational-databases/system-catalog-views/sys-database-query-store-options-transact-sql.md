---
title: sys. database_query_store_options (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5f2c8189c19fbdf6dc9a83e62117da517322df86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73983173"
---
# <a name="sysdatabase_query_store_options-transact-sql"></a>sys. database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Restituisce le opzioni di Query Store per il database.  
  
**Si applica a** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (e versioni successive [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]),.
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|Indica la modalità operativa desiderata di Query Store, impostata in modo esplicito dall'utente.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar (60)**|Descrizione testuale della modalità operativa desiderata di Query Store:<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|Indica la modalità operativa di Query Store. Oltre all'elenco degli stati desiderati richiesti dall'utente, lo stato effettivo può essere uno stato di errore.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = ERRORE|  
|**actual_state_desc**|**nvarchar (60)**|Descrizione testuale della modalità operativa effettiva di Query Store.<br />OFF<br />READ_ONLY<br />READ_WRITE<br />ERRORE<br /><br /> Esistono situazioni in cui lo stato effettivo è diverso dallo stato desiderato:<br />-Se il database è impostato sulla modalità di sola lettura o se Query Store dimensione supera la quota configurata, Query Store possibile operare in modalità di sola lettura anche se l'utente ha specificato la lettura/scrittura.<br />-In scenari estremi Query Store possibile immettere uno stato di errore a causa di errori interni. In tal caso, per SQL 2017 e versioni successive, è possibile recuperare Query Store eseguendo la `sp_query_store_consistency_check` stored procedure nel database interessato. Se l' `sp_query_store_consistency_check` esecuzione non funziona e per SQL 2016, sarà necessario cancellare i dati eseguendo`ALTER DATABASE [YourDatabaseName] SET QUERY_STORE CLEAR ALL;`|  
|**readonly_reason**|**int**|Quando il **desired_state_desc** viene READ_WRITE e il **actual_state_desc** è READ_ONLY, **readonly_reason** restituisce un mapping di bit per indicare perché il query Store è in modalità di sola lettura.<br /><br /> **1** -il database è in modalità di sola lettura<br /><br /> **2** -il database è in modalità utente singolo<br /><br /> **4** -il database è in modalità di emergenza<br /><br /> **8** : il database è una replica secondaria (si applica [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] a always on e alla replica geografica). Questo valore può essere osservato in modo efficace solo nelle repliche secondarie **leggibili**<br /><br /> **65536** : il query Store ha raggiunto il limite di dimensioni impostato dall'opzione MAX_STORAGE_SIZE_MB.<br /><br /> **131072** : il numero di istruzioni diverse in query Store ha raggiunto il limite di memoria interna. Provare a rimuovere le query che non sono necessarie o ad eseguire l'aggiornamento a un livello di servizio superiore per consentire il trasferimento di Query Store in modalità di lettura/scrittura.<br />**Si applica a:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> **262144** : le dimensioni degli elementi in memoria in attesa di essere mantenute sul disco hanno raggiunto il limite di memoria interna. Query Store sarà temporaneamente in modalità di sola lettura finché gli elementi in memoria non vengono salvati in modo permanente su disco. <br />**Si applica a:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> **524288** : il database ha raggiunto il limite di dimensioni del disco. Query Store fa parte del database utente, pertanto se non è più disponibile spazio per un database, significa che non è più possibile aumentare ulteriormente Query Store.<br />**Si applica a:** [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. <br /> <br /> Query Store per tornare alla modalità di lettura/scrittura, vedere **verificare query Store sta raccogliendo i dati delle query in modo continuativo** nella [procedura consigliata con il query Store](../../relational-databases/performance/best-practice-with-the-query-store.md#Verify).|  
|**current_storage_size_mb**|**bigint**|Dimensioni del Query Store su disco in megabyte.|  
|**flush_interval_seconds**|**bigint**|Periodo di Scaricamento normale dei dati di Query Store su disco in secondi. Il valore predefinito è **900** (15 min).<br /><br /> Modificare utilizzando l' `ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)` istruzione.|  
|**interval_length_minutes**|**bigint**|Intervallo di aggregazione delle statistiche in minuti. Non sono consentiti valori arbitrari. Usare uno dei seguenti: 1, 5, 10, 15, 30, 60 e 1440 minuti. Il valore predefinito è **60** minuti.|  
|**max_storage_size_mb**|**bigint**|Dimensioni massime del disco per il Query Store in megabyte (MB). Il valore predefinito è **100** MB.<br />Per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] l'edizione Premium, il valore predefinito è 1 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] GB e per l'edizione Basic, il valore predefinito è 10 MB.<br /><br /> Modificare utilizzando l' `ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)` istruzione.|  
|**stale_query_threshold_days**|**bigint**|Numero di giorni per cui le query senza impostazioni dei criteri vengono mantenute in Query Store. Il valore predefinito è **30**. Impostare su 0 per disabilitare i criteri di conservazione.<br />Per l'edizione [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic, l'impostazione predefinita è 7 giorni.<br /><br /> Modificare utilizzando l' `ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )` istruzione.|  
|**max_plans_per_query**|**bigint**|Limita il numero massimo di piani archiviati. Il valore predefinito è **200**. Se viene raggiunto il valore massimo, Query Store interrompe l'acquisizione dei nuovi piani per la query. Impostando su 0 viene rimossa la limitazione per quanto riguarda il numero di piani acquisiti.<br /><br /> Modificare utilizzando l' `ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)` istruzione.|  
|**query_capture_mode**|**smallint**|Modalità di acquisizione query attualmente attiva:<br /><br /> **1** = tutte le query vengono acquisite. Si tratta del valore di configurazione predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (e versioni successive).<br /><br /> 2 = Acquisisci automaticamente le query pertinenti in base al numero di esecuzioni e al consumo di risorse. Si tratta del valore di configurazione predefinito di [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].<br /><br /> 3 = NONE: interrompe l'acquisizione di nuove query. Query Store continuerà a raccogliere le statistiche di compilazione e runtime per le query che sono già state acquisite. Usare questa configurazione con cautela poiché è possibile che l'acquisizione di query importanti non venga eseguita.|  
|**query_capture_mode_desc**|**nvarchar (60)**|Descrizione testuale della modalità di acquisizione effettiva di Query Store:<br /><br /> ALL (impostazione predefinita [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]per)<br /><br /> **Auto** (impostazione predefinita [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]per)<br /><br /> Nessuno|  
|**size_based_cleanup_mode**|**smallint**|Determina se la pulizia viene attivata automaticamente quando la quantità totale dei dati ha quasi raggiunto le dimensioni massime:<br /><br /> 0 = la pulizia non basata sulle dimensioni non verrà attivata automaticamente.<br /><br /> **1** = la pulizia basata sulle dimensioni automatiche verrà attivata automaticamente quando le dimensioni su disco raggiungono il **90%** del *max_storage_size_mb*. Si tratta del valore di configurazione predefinito.<br /><br />La pulizia basata sulle dimensioni rimuove per prime le query meno recenti e meno dispendiose. Si interrompe quando viene raggiunto approssimativamente il **80%** del *max_storage_size_mb* .|  
|**size_based_cleanup_mode_desc**|**nvarchar (60)**|Descrizione testuale della modalità di pulizia effettiva basata sulle dimensioni di Query Store:<br /><br /> OFF <br /> **Automatico** (impostazione predefinita)|  
|**wait_stats_capture_mode**|**smallint**|Controlla se Query Store esegue l'acquisizione delle statistiche di attesa: <br /><br /> 0 = OFF <br /> **1** = on<br /> **Si applica a**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] e versioni successive.|
|**wait_stats_capture_mode_desc**|**nvarchar (60)**|Descrizione testuale della modalità di acquisizione delle statistiche di attesa effettiva: <br /><br /> OFF <br /> **On** (impostazione predefinita)<br /> **Si applica a**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] e versioni successive.| 
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione `VIEW DATABASE STATE`.  
  
## <a name="see-also"></a>Vedere anche  
 [sys. query_context_settings &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys. query_store_plan &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys. query_store_query &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys. query_store_query_text &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys. query_store_runtime_stats &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys. query_store_wait_stats &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys. query_store_runtime_stats_interval &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. fn_stmt_sql_handle_from_sql_stmt &#40;&#41;Transact-SQL](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [Stored procedure di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
