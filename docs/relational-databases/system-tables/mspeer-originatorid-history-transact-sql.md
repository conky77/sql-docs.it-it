---
title: MSpeer_originatorid_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95c641e094e9df405d1674c3c3c81ffa43da9d7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069055"
---
# <a name="mspeer_originatorid_history-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni ID origine definito nella topologia. Include gli ID dei nodi che non sono più attivi. La tabella viene utilizzata quando si configura un nuovo nodo per il rilevamento dei conflitti per assicurarsi che l'ID origine specificato non sia già stato utilizzato. Questa tabella è archiviata nel database di pubblicazione. Per ulteriori informazioni sul rilevamento dei conflitti, vedere [rilevamento dei conflitti nella replica peer-to-peer](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|Pubblicazione per cui è stato specificato l'ID origine.|  
|originator_id|**int**|Numero che identifica ogni nodo nella topologia per consentire il rilevamento dei conflitti.|  
|originator_node|**sysname**|Istanza del server per cui è stato specificato l'ID origine.|  
|originator_db|**sysname**|Database di pubblicazione per cui è stato specificato l'ID origine.|  
|originator_db_version|**int**|Identifica il numero di versione del database di origine.|  
|originator_version|**int**|Identifica il numero di versione del server di pubblicazione.|  
|inserted_date|**datetime**|Data e ora in cui la riga per l'ID origine è stata inserita in questa tabella.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
