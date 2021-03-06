---
title: Apportare modifiche alle tabelle selezionate per l'acquisizione di modifiche | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- makChanToTab
ms.assetid: a309f82a-c6ef-464d-a6ef-df555bfb609a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7ee52054e14c641aad64eaa96b146af86e048d95
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298698"
---
# <a name="make-changes-to-the-tables-selected-for-capturing-changes"></a>Apportare modifiche alle tabelle selezionate per l'acquisizione di modifiche

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  In questa finestra di dialogo è possibile selezionare colonne specifiche della tabella selezionata da cui acquisire le modifiche. È anche possibile modificare le informazioni **Security Role** e **Capture Instance** .  
  
 È possibile apportare le modifiche seguenti alle tabelle selezionate per l'acquisizione delle modifiche in questa finestra di dialogo.  
  
 **Cambiare le colonne incluse nell'istanza di CDC:**  
  
 Eseguire una o entrambe le operazioni seguenti:  
  
-   Selezionare la casella di controllo accanto a eventuali colonne aggiuntive che si desidera includere.  
  
-   Deselezionare la casella di controllo accanto alle colonne che non si desidera più includere.  
  
 **Modificare il tipo di dati per una colonna specifica**:  
  
 È possibile selezionare un tipo di dati diverso per una colonna specifica. È possibile solo modificare il tipo di dati su un tipo di dati compatibile con il tipo di dati originale.  
  
 Per modificare il tipo di dati, fare clic nella colonna **Tipo di dati** e selezionare un tipo di dati diverso. Sono disponibili solo i tipi di dati compatibili con il tipo di dati originale.  
  
> [!NOTE]  
>  Se non è possibile selezionare tipi di dati aggiuntivi, l'elenco a discesa non è disponibile.  
  
 **Modificare il ruolo di sicurezza**  
  
 Digitare un nuovo nome oppure modificare il nome esistente del ruolo di sicurezza nel campo **Ruolo di sicurezza** .  
  
 **Modificare o aggiungere un'istanza di acquisizione**  
  
 Nel campo **Istanza di acquisizione** immettere un nome per l'istanza di acquisizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura di creazione dell'istanza del database delle modifiche di SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Selezionare tabelle e colonne Oracle](../../integration-services/change-data-capture/select-oracle-tables-and-columns.md)  
  
  
