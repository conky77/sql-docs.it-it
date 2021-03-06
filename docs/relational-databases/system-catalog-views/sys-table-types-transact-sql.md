---
title: sys. table_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- table_types_TSQL
- sys.table_types
- sys.table_types_TSQL
- table_types
dev_langs:
- TSQL
helpviewer_keywords:
- table types [SQL Server]
- table-valued parameters, sys.table_types
- sys.table_types
- UDTT
ms.assetid: c05fd873-aff2-4a89-9936-a54c2ea09996
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bc4e77bd978432bf6e1e11930c121e0e7fc6b6ea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73982107"
---
# <a name="systable_types-transact-sql"></a>sys.table_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Visualizza le proprietà dei tipi di tabella definiti dall'utente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un tipo di tabella è un tipo dal quale potrebbero essere dichiarati variabili della tabella o parametri con valori di tabella. Ogni tipo di tabella dispone di un **type_table_object_id** che rappresenta una chiave esterna nella vista del catalogo [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) . È possibile utilizzare questa colonna ID per eseguire query su varie viste del catalogo, in modo analogo a una colonna **object_id** di una normale tabella, per individuare la struttura del tipo di tabella, ad esempio le colonne e i vincoli.    
 
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|*\<colonne ereditate>*||Per un elenco delle colonne ereditate da questa vista, vedere [sys. types &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-types-transact-sql.md).|  
|**type_table_object_id**|**int**|Numero di identificazione dell'oggetto. Numero univoco all'interno di un database.|  
|**is_memory_optimized**|**bit**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] e versioni successive.<br /><br /> Di seguito sono indicati i valori possibili:<br /><br /> 0 = senza ottimizzazione per la memoria<br /><br /> 1 = con ottimizzazione per la memoria<br /><br /> Il valore predefinito è 0.<br /><br /> I tipi di tabella vengono sempre creati con DURABILITY = SCHEMA_ONLY. Solo lo schema è persistente su disco.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo oggetti &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Utilizzare parametri con valori di tabella &#40;motore di database&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
