---
title: Tipo di sottoscrizione | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d936c1a1086f13d43bc38758f86a0ab80f757f7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63249374"
---
# <a name="subscription-type"></a>Tipo di sottoscrizione
  La replica di tipo merge offre due tipi di sottoscrizione: server e client (indicati rispettivamente [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nelle versioni precedenti di come globale e locale). I Sottoscrittori con una sottoscrizione di tipo server sono in grado di:  
  
-   Ripubblicare i dati di altri Sottoscrittori.  
  
-   Fungere da partner di sottoscrizione alternativi.  
  
-   Risolvere conflitti in base alla priorità impostata.  
  
 La maggior parte dei Sottoscrittori non necessita di questa funzionalità ed è in grado di utilizzare una sottoscrizione client. Le sottoscrizioni client consentono ancora il rilevamento e la risoluzione dei conflitti, ma ai Sottoscrittori non viene assegnata una priorità. In altre parole, il primo Sottoscrittore che inoltra una modifica al server di pubblicazione prevale nei conflitti eventualmente generati da tale modifica.  
  
> [!NOTE]  
>  Dopo aver creato la sottoscrizione non è possibile modificarne il tipo.  
  
## <a name="options"></a>Opzioni  
 **Proprietà sottoscrizione**  
 Per ogni Sottoscrittore, selezionare **Client** o **Server** nell'elenco a discesa nella colonna **Tipo di sottoscrizione** . Per i Sottoscrittori con sottoscrizioni server, immettere un numero compreso tra 0 e 99,99 nella colonna **Priorità per la risoluzione dei conflitti** . Maggiore è questo numero, più alta è la priorità per il Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Sottoscrizione delle pubblicazioni](subscribe-to-publications.md)  
  
  
