---
title: Modelli (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], about models
- models [Master Data Services]
ms.assetid: 9f862a3d-25ab-41e9-b833-1db99959e825
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d202c04a41553b934c175edb7c0afcd907e846e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482542"
---
# <a name="models-master-data-services"></a>Modelli (Master Data Services)
  I modelli rappresentano il livello più elevato di organizzazione dei dati in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Un modello definisce la struttura di dati nella soluzione di gestione dati master. Un modello contiene gli oggetti seguenti:  
  
-   Entità  
  
-   Attributi e gruppi di attributi  
  
-   Gerarchie derivate ed esplicite  
  
-   Raccolte  
  
 I modelli organizzano la struttura dei dati master. L'implementazione di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] può avere uno o più modelli che raggruppano tipi di dati simili. I dati master rientrano in genere in una delle quattro categorie seguenti: persone, luoghi, cose o concetti. È ad esempio possibile creare un modello Product per contenere dati relativi al prodotto oppure un modello Customer per contenere dati relativi al cliente.  
  
 È possibile assegnare le autorizzazioni di utenti e gruppi per visualizzare e aggiornare oggetti all'interno del modello. Se non si assegnano autorizzazioni al modello, questo non verrà visualizzato.  
  
 In qualsiasi momento è possibile creare copie dei dati master all'interno di un modello. Queste copie sono denominate versioni.  
  
 Dopo aver definito un modello in un ambiente di prova, è possibile distribuirlo, con o senza i dati corrispondenti, dall'ambiente di prova in un ambiente di produzione. In questo modo viene eliminata la necessità di ricreare i modelli nell'ambiente di produzione.  
  
## <a name="how-models-relate-to-other-objects"></a>Correlazione tra modelli e altri oggetti  
 Un modello contiene entità. Le entità contengono attributi, gerarchie esplicite e raccolte. È possibile contenere gli attributi in gruppi di attributi. Gli attributi si dicono basati su dominio quando un'entità viene utilizzata come un attributo per un'altra entità.  
  
 La seguente immagine illustra la relazione tra gli oggetti di un modello.  
  
 ![Oggetti in un modello Master Data Services](../../2014/master-data-services/media/mds-conc-model-circles.gif "Oggetti in un modello Master Data Services")  
  
> [!NOTE]  
>  Anche le gerarchie derivate sono oggetti modello, ma non sono presenti nell'immagine. Le gerarchie derivate sono basate sulle relazioni tra gli attributi basati su dominio che esistono in un modello. Vedere [Gerarchie derivate &#40;Master Data Services&#41;](derived-hierarchies-master-data-services.md) per altre informazioni.  
  
 I dati master sono i dati contenuti negli oggetti modello. In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], i dati master vengono archiviati come membri all'interno di un'entità.  
  
 Gli oggetti modello vengono gestiti nell'area funzionale **Amministrazione sistema** dell'interfaccia utente di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## <a name="model-example"></a>Esempio di modello  
 Nell'esempio seguente, gli oggetti del modello Product raggruppano in modo logico i dati relativi al prodotto.  
  
 ![Esempio di dati master del modello del prodotto](../../2014/master-data-services/media/mds-conc-model.gif "Esempio di dati master del modello del prodotto")  
  
 Altri modelli comuni sono:  
  
-   Conti, che potrebbe includere entità quali conti patrimoniali, conti economici, statistiche e tipo di conto.  
  
-   Cliente, che potrebbe includere entità quale genere, livello di istruzione, occupazione e stato civile.  
  
-   Geografia, che potrebbe includere entità quali codici postali, paesi, città, province, regioni, stati e continenti.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare un modello per organizzare i dati master.|[Creazione di un modello &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-model-master-data-services.md)|  
|Modificare il nome di un modello esistente.|[Modificare il nome di un modello &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-model-name-master-data-services.md)|  
|Eliminare un modello esistente.|[Eliminare un modello &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-model-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Panoramica di Master Data Services](master-data-services-overview-mds.md)  
  
-   [Entità &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)  
  
-   [Attributi &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md)  
  
-   [Distribuzione di modelli &#40;Master Data Services&#41;](../../2014/master-data-services/deploying-models-master-data-services.md)  
  
-   [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md)  
  
  
