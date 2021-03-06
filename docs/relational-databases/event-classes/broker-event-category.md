---
title: Categoria di eventi Broker | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8efa6f503f552965e3885d92626e8b5da453e29b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "69494089"
---
# <a name="broker-event-category"></a>Categoria di eventi Broker

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

La categoria di eventi **Broker** include gli eventi generali di Service Broker.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Classe di evento Broker:Activation](../../relational-databases/event-classes/broker-activation-event-class.md)|Evento generato quando un monitoraggio di coda avvia una stored procedure di attivazione.|  
|[Classe di evento Broker:Connection](../../relational-databases/event-classes/broker-connection-event-class.md)|Evento generato per indicare lo stato di una connessione di trasporto gestita da Service Broker.|  
|[Classe di evento Broker:Conversation](../../relational-databases/event-classes/broker-conversation-event-class.md)|Evento generato per indicare lo stato di una conversazione.|  
|[Classe di evento Broker:Conversation Group](../../relational-databases/event-classes/broker-conversation-group-event-class.md)|Evento generato quando il database crea o elimina un gruppo di conversazione.|  
|[Classe di evento Broker:Corrupted Message](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)|Evento generato per indicare che il database ha ricevuto un messaggio danneggiato.|  
|[Classe di evento Broker:Forwarded Message Dropped](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)|Evento generato quando SQL Server elimina un messaggio di Service Broker per cui era previsto l'inoltro.|  
|[Classe di evento Broker:Forwarded Message Sent](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)|Evento generato quando SQL Server inoltra un messaggio di Service Broker.|  
|[Classe di evento Broker:Message Classify](../../relational-databases/event-classes/broker-message-classify-event-class.md)|Evento generato quando Service Broker stabilisce il routing di un messaggio.|  
|[Classe di evento Broker:Message Drop](../../relational-databases/event-classes/broker-message-drop-event-class.md)|Evento generato quando Service Broker non è in grado di memorizzare un messaggio ricevuto che avrebbe dovuto essere recapitato a un servizio nell'istanza corrente.|  
|[Classe di evento Broker:Remote Message Ack](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|Evento generato quando Service Broker invia o riceve l'acknowledgement di un messaggio.|  
  
 Vengono inoltre generati due eventi di controllo della sicurezza per Service Broker. Per altre informazioni sugli eventi, vedere [Classe di evento Audit Broker Login](../../relational-databases/event-classes/audit-broker-login-event-class.md) e [Classe di evento Audit Broker Conversation](../../relational-databases/event-classes/audit-broker-conversation-event-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi Controllo di sicurezza](/bi-reference/trace-events/security-audit-event-category)  
  
  
