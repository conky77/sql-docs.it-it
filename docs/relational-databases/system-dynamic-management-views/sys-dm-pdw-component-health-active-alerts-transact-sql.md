---
title: sys. dm_pdw_component_health_active_alerts (Transact-SQL
ms.custom: seo-dt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 90531889d3e510d342ff39abdf069f75f3c371aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401717"
---
# <a name="sysdm_pdw_component_health_active_alerts-transact-sql"></a>sys. dm_pdw_component_health_active_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Archivia gli avvisi attivi [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] sui componenti.  
  
|Nome colonna|Tipo di dati|Descrizione|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Identificatore univoco di un [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nodo.<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id e alert_instance_id costituiscono la chiave per questa visualizzazione.|NOT NULL|  
|component_id|**int**|ID del componente. Vedere [sys. pdw_health_components &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id e alert_instance_id costituiscono la chiave per questa visualizzazione.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, component_id, component_instance_id, alert_id e alert_instance_id costituiscono la chiave per questa visualizzazione.|NOT NULL|  
|alert_id|**int**|ID per il tipo di avviso. Vedere [sys. pdw_health_alerts &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id e alert_instance_id costituiscono la chiave per questa visualizzazione.|NOT NULL|  
|alert_instance_id|**nvarchar (36)**|Identifica un'istanza di un determinato avviso.<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id e alert_instance_id costituiscono la chiave per questa visualizzazione.|NOT NULL|  
|current_value|**nvarchar(255)**|Utilizzato quando l'avviso è di tipo StatusChange. Questo è lo stato del componente corrente. Il valore è NULL per gli avvisi di tipo soglia. Vedere [sys. pdw_health_alerts &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) per un elenco di tipi di avviso.|NULL|  
|previous_value|**nvarchar(255)**|Utilizzato quando l'avviso è di tipo StatusChange. Questo è lo stato del componente precedente. Il valore è NULL per gli avvisi di tipo soglia. Vedere [sys. pdw_health_alerts &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) per un elenco di tipi di avviso.|NULL|  
|create_time|**datetime**|Data e ora di generazione dell'avviso.|NOT NULL|  
  
 Per informazioni sul numero massimo di righe mantenute da questa visualizzazione, vedere "valori minimi e massimi [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]" in.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel data warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
