---
title: sys. transmission_queue (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- transmission_queue
- sys.transmission_queue_TSQL
- sys.transmission_queue
- transmission_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.transmission_queue catalog view
ms.assetid: f3515d1a-be8f-4a27-8058-8865f0919838
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7bd461a677a7bfab145846baaf09c0a8a62d6f8b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022604"
---
# <a name="systransmission_queue-transact-sql"></a>sys.transmission_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa vista del catalogo contiene una riga per ogni messaggio nella coda di trasmissione, come illustrato nella tabella seguente:  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**conversation_handle**|**uniqueidentifier**|Identificatore per la conversazione a cui appartiene il messaggio. Non ammette i valori Null.|  
|**to_service_name**|**nvarchar(256)**|Nome del servizio a cui è destinato il messaggio. Ammette valori Null.|  
|**to_broker_instance**|**nvarchar(128)**|Identificatore del broker che ospita il servizio a cui è destinato il messaggio. Ammette valori Null.|  
|**from_service_name**|**nvarchar(256)**|Nome del servizio da cui proviene il messaggio. Ammette valori Null.|  
|**service_contract_name**|**nvarchar(256)**|Nome del contratto rispettato dalla conversazione per il messaggio. Ammette valori Null.|  
|**enqueue_time**|**datetime**|Ora in cui il messaggio ha raggiunto la coda. Questo valore utilizza l'ora UTC (Coordinated Universal Time o ora di Greenwich) indipendentemente dal fuso orario locale per l'istanza. Non ammette i valori Null.|  
|**message_sequence_number**|**bigint**|Numero di sequenza del messaggio. Non ammette i valori Null.|  
|**message_type_name**|**nvarchar(256)**|Nome del tipo di messaggio per il messaggio. Ammette valori Null.|  
|**is_conversation_error**|**bit**|Indica se il messaggio è un messaggio di errore.<br /><br /> 0 = Non è un messaggio di errore.<br /><br /> 1 = Messaggio di errore.<br /><br /> Non ammette i valori Null.|  
|**is_end_of_dialog**|**bit**|Indica se il messaggio è un messaggio di fine conversazione. Non ammette i valori Null.<br /><br /> 0 = Non è un messaggio di fine conversazione.<br /><br /> 1 = Messaggio di fine conversazione.<br /><br /> Non ammette i valori Null.|  
|**message_body**|**varbinary(max)**|Corpo del messaggio. Ammette valori Null.|  
|**transmission_status**|**nvarchar(4000)**|Motivo per cui il messaggio si trova nella coda. Di solito è un messaggio di errore che illustra perché l'invio del messaggio non è riuscito. Se non contiene alcun valore, il messaggio non è ancora stato inviato. Ammette valori Null.|  
|**priorità**|**tinyint**|Livello di priorità assegnato al messaggio. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
