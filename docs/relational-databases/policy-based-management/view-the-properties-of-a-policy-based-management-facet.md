---
title: Visualizzare le proprietà di un facet della gestione basata su criteri
description: Informazioni su come visualizzare le proprietà di un facet della gestione basata su criteri in SQL Server tramite SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facet properties
ms.assetid: 022a244c-c2e7-4467-b9a2-c7a27859be22
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3a5a938928817b8ffb5282b2af7d2a505b442302
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "75558096"
---
# <a name="view-the-properties-of-a-policy-based-management-facet"></a>Visualizzare le proprietà di un facet della gestione basata su criteri
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento verrà descritto come visualizzare le proprietà di un facet della gestione basata su criteri in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare le proprietà di un facet tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-view-the-properties-of-a-facet"></a>Per visualizzare le proprietà di un facet  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server contenente il facet di cui si desidera visualizzare le proprietà.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic sul segno più per espandere la cartella **Facet** .  
  
5.  Fare clic con il pulsante destro del mouse sul facet di cui si vogliono visualizzare le proprietà e scegliere **Proprietà**. Per altre informazioni sulle opzioni disponibili nella finestra di dialogo **Proprietà facet -** _nome_facet_, vedere [Finestra di dialogo Proprietà facet, pagina Generale](../../relational-databases/policy-based-management/facet-properties-dialog-box-general-page.md), [Finestra di dialogo Proprietà facet, pagina Criteri dipendenti](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-policies-page.md) e [Finestra di dialogo Proprietà facet, pagina Condizioni dipendenti](../../relational-databases/policy-based-management/facet-properties-dialog-box-dependent-conditions-page.md).  
  
6.  Al termine, fare clic su **Chiudi**.  

