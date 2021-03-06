---
title: sys. change_tracking_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- change_tracking_databases
- sys.change_tracking_databases_TSQL
- sys.change_tracking_databases
- change_tracking_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.change_tracking_databases
- change tracking [SQL Server], sys.change_tracking_databases
ms.assetid: bb233baa-2991-4904-a0eb-3772b81121a4
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9d3f2f92e9be7b6d4f38edff7cb36aa67e055788
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68136544"
---
# <a name="change-tracking-catalog-views---syschange_tracking_databases"></a>Viste del catalogo Rilevamento modifiche-sys. change_tracking_databases
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni database con il rilevamento delle modifiche abilitato.  

|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database. È univoco all'interno dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|is_auto_cleanup_on|**bit**|Indica se i dati di rilevamento delle modifiche vengono rimossi automaticamente una volta trascorso il periodo di memorizzazione configurato:<br /><br /> 0 = Off<br /><br /> 1 = On|  
|retention_period|**int**|Se si utilizza la rimozione automatica, il periodo di memorizzazione specifica per quanto tempo i dati di rilevamento delle modifiche verranno conservati nel database.|  
|retention_period_units_desc|**nvarchar (60)**|Specifica la descrizione del periodo memorizzazione:<br /><br /> Minuti<br /><br /> Ore<br /><br /> Days|  
|retention_period_units|**tinyint**|Unità di tempo relativa al periodo di memorizzazione:<br /><br /> 1 = Minuti<br /><br /> 2 = Ore<br /><br /> 3 = Giorni|  
  
## <a name="permissions"></a>Autorizzazioni  
 Gli stessi controlli dell'autorizzazione vengono effettuati per sys.change_tracking_databases, così come per sys.databases. Se il chiamante di sys.change_tracking_databases non è il proprietario del database, le autorizzazioni minime necessarie per visualizzare la riga corrispondente sono ALTER ANY DATABASE o VIEW ANY DATABASE a livello di server, oppure l'autorizzazione CREATE DATABASE nel database master o corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di Rilevamento modifiche &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Rilevare le modifiche ai dati &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
