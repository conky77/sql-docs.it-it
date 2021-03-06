---
title: MSmerge_genhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_genhistory_TSQL
- MSmerge_genhistory
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_genhistory system table
ms.assetid: 475d08ae-eb8b-49de-afd6-33c96ab8004d
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf9c38fe71c1282b19b947fc1771714dd138c45a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017697"
---
# <a name="msmerge_genhistory-transact-sql"></a>MSmerge_genhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La tabella **MSmerge_genhistory** contiene una riga per ogni generazione che un Sottoscrittore conosce (entro il periodo di conservazione). Viene utilizzata per evitare l'invio di generazioni comuni durante operazioni di scambio e per risincronizzare i Sottoscrittori ripristinati dai backup. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**guidsrc**|**uniqueidentifier**|Identificatore globale delle modifiche identificate dalla generazione nel Sottoscrittore.|  
|**pubid**|**uniqueidentifier**|Identificatore della pubblicazione.|  
|**generazione**|**bigint**|Valore di generazione.|  
|**art_nick**|**int**|Nome alternativo dell'articolo.|  
|**nicknames**|**varbinary (1001)**|Elenco di nomi alternativi degli altri Sottoscrittori in cui questa generazione è già presente. Viene utilizzato per evitare l'invio di una generazione a un Sottoscrittore in cui tali modifiche sono già state applicate. L'elenco di nomi alternativi viene mantenuto ordinato per ottimizzare le operazioni di ricerca. Se vi sono altri nomi alternativi da aggiungere a questo campo, essi non trarranno beneficio da tale ottimizzazione.|  
|**coldate**|**datetime**|Data in cui la generazione corrente è stata aggiunta alla tabella.|  
|**genstatus**|**tinyint**|Lo stato della generazione è il seguente:<br /><br /> **0** = aperto.<br /><br /> **1** = chiuso.<br /><br /> **2** = chiuso e originato in un altro Sottoscrittore.|  
|**changecount**|**int**|Numero delle modifiche già applicate in una specifica generazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
