---
title: Assegnare autorizzazioni per oggetti modello
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], assigning object permissions
- permissions [Master Data Services], assigning model object permissions
ms.assetid: 4b80148d-2318-415c-9479-28c240e48bcd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a6c1dbc6be8ba8ddde53ea1ccdfa97fe7992a4b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728745"
---
# <a name="assign-model-object-permissions-master-data-services"></a>Assegnare autorizzazioni per oggetti modello (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]assegnare autorizzazioni agli oggetti modello quando è necessario concedere un accesso utente o gruppo ai dati nell'area funzionale **Esplora** di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]o quando è necessario rendere un utente o un gruppo un amministratore.  
  
> [!NOTE]  
>  Quando si assegna l'autorizzazione per un modello, viene implicitamente negata l'autorizzazione per tutti gli altri modelli. La mancata assegnazione di autorizzazioni dell'oggetto modello determina l'impossibilità da parte dell'utente o gruppo di accedere ai dati in **Esplora**.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Autorizzazioni utenti e gruppi** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-assign-model-object-permissions"></a>Per assegnare autorizzazioni dell'oggetto modello  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Autorizzazioni utenti e gruppi**.  
  
2.  Nella pagina **Utenti** o **Gruppi** selezionare la riga relativa all'utente o al gruppo che si desidera modificare.  
  
3.  Fare clic su **Modifica utente selezionato**.  
  
4.  Fare clic sulla scheda **Modelli** .  
  
5.  Facoltativamente selezionare un modello nell'elenco **Modello** .  
  
6.  Fare clic su **Edit**.  
  
7.  Espandere l'albero e selezionare l'oggetto modello al quale si desidera assegnare le autorizzazioni.  
  
8.  Nel menu selezionare una combinazione di Lettura, Creazione, Aggiornamento ed Eliminazione oppure Nega.  
  
9. Al livello superiore del modello selezionare **Amministratore** se è necessario impostare un modello utente come amministratore.  
  
10. Fare clic su **Salva**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   (Facoltativo) [Assegnare autorizzazioni membri gerarchia &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Elimina autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/delete-model-object-permissions-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Creare un amministratore di modelli &#40;Master Data Services&#41;](../master-data-services/create-a-model-administrator-master-data-services.md)  
  
  
