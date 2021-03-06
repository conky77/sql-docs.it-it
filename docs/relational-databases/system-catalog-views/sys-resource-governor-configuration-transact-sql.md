---
title: sys. resource_governor_configuration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_configuration_TSQL
- sys.resource_governor_configuration
- resource_governor_configuration_TSQL
- resource_governor_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_configuration catalog view
ms.assetid: 89099668-1dc6-4b07-9d8b-49bc95c7bfc0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e4068d9763460995335fe5adbd6684ecb70d8b7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73982622"
---
# <a name="sysresource_governor_configuration-transact-sql"></a>sys.resource_governor_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce lo stato di Resource Governor memorizzato.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|ID della funzione di classificazione memorizzata nei metadati. Non ammette i valori Null.<br /><br /> **Nota** Questa funzione viene utilizzata per classificare le nuove sessioni e utilizza le regole per instradare il carico di lavoro al gruppo di carico di lavoro appropriato. Per altre informazioni, vedere [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).|  
|is_enabled|**bit**|Indica lo stato corrente di Resource Governor:<br /><br /> 0 = Resource Governor non è abilitato.<br /><br /> 1 = Resource Governor è abilitato.<br /><br /> Non ammette i valori Null.|  
|max_outstanding_io_per_volume|**int**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e versioni successive.<br /><br /> Numero massimo di operazioni di I/O in sospeso per volume.|  
  
## <a name="remarks"></a>Osservazioni  
 La vista del catalogo visualizza la configurazione di Resource Governor memorizzata nei metadati. Per vedere la configurazione in memoria utilizzare la vista a gestione dinamica corrispondente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede l'autorizzazione VIEW ANY DEFINITION per visualizzare i contenuti e l'autorizzazione CONTROL SERVER per modificarli.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come ottenere e confrontare i valori dei metadati archiviati e i valori in memoria della configurazione di Resource Governor.  
  
```  
USE master;  
GO  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
GO  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di Resource Governor &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. dm_resource_governor_configuration &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql.md)   
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)  
  
  
