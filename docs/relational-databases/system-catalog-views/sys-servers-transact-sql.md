---
title: sys. Servers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- servers_TSQL
- sys.servers_TSQL
- servers
- sys.servers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.servers catalog view
ms.assetid: 4e774ed9-4e83-4726-9f1d-8efde8f9feff
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b17296d558c078d3f580e63bf662bb975615ad94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132953"
---
# <a name="sysservers-transact-sql"></a>sys.servers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Contiene una riga per ogni server collegato o remoto registrato e una riga per il server locale con **server_id** = 0.  

|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID locale del server collegato.|  
|**nome**|**sysname**|Quando **server_id** = 0, il valore restituito è il nome del server.<br /><br /> Quando **server_id** > 0, il valore restituito è il nome locale del server collegato.|  
|**prodotto**|**sysname**|Nome del prodotto del server collegato. Il valore "SQL Server" indica un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**provider**|**sysname**|Nome del provider OLE DB per la connessione al server collegato.|  
|**data_source**|**nvarchar(4000)**|Proprietà di connessione dell'origine dei dati OLE DB.|  
|**percorso**|**nvarchar(4000)**|Proprietà di connessione della posizione OLE DB. Restituisce NULL se la colonna non include alcun valore.|  
|**provider_string**|**nvarchar(4000)**|Proprietà di connessione della stringa del provider OLE DB.<br /><br /> È NULL tranne nei casi in cui il chiamante dispone dell'autorizzazione ALTER ANY LINKED SERVER.|  
|**Catalogo**|**sysname**|Proprietà di connessione del catalogo OLE DB. Restituisce NULL se la colonna non include alcun valore.|  
|**connect_timeout**|**int**|Timeout della connessione espresso in secondi. Restituisce 0 se non si specifica alcun valore.|  
|**query_timeout**|**int**|Timeout della query espresso in secondi. Restituisce 0 se non si specifica alcun valore.|  
|**is_linked**|**bit**|0 = è un server obsoleto aggiunto tramite **sp_addserver**, con diversi comportamenti RPC e Distributed-Transaction.<br /><br /> 1 = Server collegato standard.|  
|**is_remote_login_enabled**|**bit**|L'opzione RPC è impostata per consentire gli accessi remoti in entrata per questo server.|  
|**is_rpc_out_enabled**|**bit**|Sono abilitate le chiamate RPC in uscita (da questo server).|  
|**is_data_access_enabled**|**bit**|Il server è abilitato per le query distribuite.|  
|**is_collation_compatible**|**bit**|Le regole di confronto dei dati remoti vengono considerate compatibili con i dati locali se non sono disponibili informazioni sulle regole di confronto.|  
|**uses_remote_collation**|**bit**|Il valore 1 indica che vengono utilizzate le regole di confronto segnalate dal server remoto. In caso contrario, vengono utilizzate le regole di confronto specificate dalla colonna successiva.|  
|**collation_name**|**sysname**|Nome delle regole di confronto da utilizzare oppure NULL se vengono utilizzate le regole di confronto locali.|  
|**lazy_schema_validation**|**bit**|Il valore 1 indica che la convalida dello schema non viene verificata all'avvio della query.|  
|**is_system**|**bit**|È possibile accedere a questo server solo dal sistema interno.|  
|**is_publisher**|**bit**|Il server è un server di pubblicazione per la replica.|  
|**is_subscriber**|**bit**|Il server è un Sottoscrittore per la replica.|  
|**is_distributor**|**bit**|Il server è un server di distribuzione per la replica.|  
|**is_nonsql_subscriber**|**bit**|Il server è un Sottoscrittore non SQL Server per la replica.|  
|**is_remote_proc_transaction_promotion_enabled**|**bit**|Se 1, la chiamata di una stored procedure remota comporta l'avvio di una transazione distribuita e l'integrazione della transazione in MS DTC. Per altre informazioni, vedere [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md).|  
|**modify_date**|**datetime**|Data dell'ultima modifica delle informazioni relative al server.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Il valore nel **provider_string** è sempre null, a meno che il chiamante disponga dell'autorizzazione ALTER ANY Linked Server.  
  
 Non sono necessarie autorizzazioni per visualizzare il server locale (**server_id** = 0).  
  
 Quando si crea un server collegato o remoto, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in viene creato un mapping di account di accesso predefinito al ruolo del server **public** . Il mapping predefinito degli account di accesso indica che tutti gli account di accesso possono visualizzare tutti i server collegati e remoti. Per limitare la visibilità a questi server, rimuovere il mapping predefinito degli account di accesso eseguendo [sp_droplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md) e specificando null per il parametro *locallogin* .  
  
 Se il mapping predefinito degli account di accesso viene eliminato, solo gli utenti aggiunti esplicitamente come account di accesso collegato o remoto possono visualizzare i server collegati o remoti per cui dispongono di un account di accesso.  Per visualizzare tutti i server collegati e remoti dopo il mapping predefinito degli account di accesso, sono necessarie le autorizzazioni seguenti:  
  
- `ALTER ANY LINKED SERVER`o`ALTER ANY LOGIN ON SERVER`  
- Appartenenza ai ruoli predefiniti del server **setupadmin** o **sysadmin**  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo di server collegati &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addremotelogin &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)  
  
  
