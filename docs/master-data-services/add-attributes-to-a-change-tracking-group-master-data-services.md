---
title: Aggiungere attributi a un gruppo di Rilevamento modifiche
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ac3f582767e3df524716f92ea4d57e53cb7b9246
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728812"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a>Aggiungere attributi ad un gruppo rilevamento modifiche (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]aggiungere attributi a un gruppo rilevamento modifiche quando si vuole tenere traccia delle modifiche apportate ai valori dell'attributo.  
  
> [!NOTE]  
>  In seguito all'aggiunta di un attributo a un gruppo rilevamento modifiche, quando si modificano i valori relativi a tale attributo, l'attributo viene contrassegnato nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Creare una regola business per eseguire le azioni appropriate in base alla modifica.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   È necessario che esistano degli attributi da aggiungere al gruppo rilevamento modifiche. Per altre informazioni, vedere [Creare un attributo di testo &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a>Per aggiungere attributi ad un gruppo rilevamento modifiche  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modello** selezionare un modello dalla griglia e quindi fare clic su **entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga dell'entità per la quale si vuole creare un attributo.  
  
4.  Fare clic su **Attributi**.  
  
5.  Nella pagina **Gestisci attributi** eseguire una delle operazioni seguenti.  
  
    -   Se l'attributo è per i membri foglia, selezionare **Foglia** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per i membri consolidati, selezionare **Consolidato** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per le raccolte, selezionare **Raccolta** nella casella di riepilogo **Tipo di membro** .  
  
6.  Selezionare la riga per l'attributo che si vuole modificare e quindi fare clic su **Modifica**.  
  
7.  Selezionare la casella di controllo **Abilita rilevamento modifiche** .  
  
8.  Nella casella **Gruppo rilevamento modifiche** digitare un numero per il gruppo.  
  
9. Fare clic su **Salva attributo**.  
  
     Per l'attributo modificato, la colonna del gruppo **Abilita rilevamento modifiche** nella griglia viene modificata in **Sì (gruppo: numero del gruppo immesso)**.  
  
10. Ripetere questa procedura per tutti gli attributi che si desidera includere nel gruppo. Utilizzare lo stesso numero del gruppo rilevamento modifiche per ciascun attributo del gruppo.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   [Avviare azioni in base alle modifiche del valore dell'attributo &#40;Master Data Services&#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un attributo di testo &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
