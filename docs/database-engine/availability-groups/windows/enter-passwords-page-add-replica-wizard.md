---
title: 'Procedura guidata Aggiungi replica: Pagina Immetti password per i gruppi di disponibilità'
description: Descrizione delle proprietà disponibili nella pagina Immetti password della procedura guidata Aggiungi replica di SQL Server Management Studio.
ms.custom: seo-lt-2019
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.addreplicawizard.enterpasswords.f1
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6277498bd66e2659e0a692d2e62d66501ca1fac8
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "74822212"
---
# <a name="enter-passwords-page-add-replica-wizard-for-always-on-availability-groups"></a>Pagina Immetti password (Aggiungi replica) per i gruppi di disponibilità Always On
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Questo argomento della Guida descrive le opzioni della pagina **Immetti password** . Questo argomento si applica alla [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Se le repliche selezionate nella pagina **Specifica repliche** contengono database con una chiave master del database, viene visualizzata la pagina Immetti password.  
  
## <a name="enter-passwords-options"></a>Opzioni Immetti password  
 Nella griglia **Database utente in questa istanza di SQL Server** è elencato ogni database utente locale. Le colonne sono le seguenti:  
  
 **Nome**  
 Visualizza il nome di un database utente locale.  
  
 **Dimensione**  
 Visualizza la dimensione del database, se è disponibile per la procedura guidata.  
  
 **Status**  
 Indica **Password obbligatoria** per i database con una chiave master del database. Dopo avere immesso la password per le chiavi master di database nella colonna **Password** , fare clic su **Aggiorna**. Se le password sono state immesse correttamente, la colonna **Stato** visualizza **Password immessa**.  
  
 Se il database non ha una chiave master di database, la colonna **Stato** visualizza **Password non obbligatoria**.  
  
 **Password**  
 Se la colonna **Stato** visualizza **Password obbligatoria**, immettere la password per la chiave master del database.  
  
 **Aggiorna**  
 Fare clic per aggiornare la griglia. Ciò è utile dopo avere immesso le password necessarie.  
  
## <a name="related-tasks"></a>Attività correlate  
  
-   [Usare la procedura guidata Aggiungi replica a gruppo di disponibilità &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Prerequisiti, restrizioni e consigli per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
