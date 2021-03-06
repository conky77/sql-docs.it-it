---
title: 'Attività 8: creazione di una regola di dominio composito | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: cff3b662-7876-4445-9bdd-96be35b3ca0c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7e40ec982a9b2c43c3d55ec60179ac9a0b80e8a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "65489621"
---
# <a name="task-8-creating-a-composite-domain-rule"></a>Attività 8: Creazione di una regola per un dominio composito
  In questa attività viene creata una regola per il dominio composito **Address Validation** . Si definisce una regola tra domini: se **City** è **Los Angeles**, **state** deve essere **CA** , dove **City** e **state** sono due domini.  
  
1.  Nel riquadro destro passare alla scheda **CD Rules (regole CD** ).  
  
2.  Fare clic su **Aggiungi una nuova regola di dominio** dalla barra degli strumenti.  
  
3.  Digitare **City-State Rule** per **Name** e premere **invio**.  
  
4.  Nel riquadro **Compila una regola** selezionare **città** nell'elenco di domini e selezionare la condizione il **valore è uguale a** e digitare **Los Angeles** come valore.  
  
5.  Nel riquadro **then** selezionare **stato** nell'elenco dominio e selezionare il **valore è uguale a**, digitare **CA** come valore e premere **Tab**.  
  
     ![Regola dominio composito](../../2014/tutorials/media/et-creatingacompositedomainrule.jpg "Regola dominio composito")  
  
6.  Fare clic sul pulsante **Chiudi** nella parte inferiore della pagina per passare alla pagina principale del client DQS. Nella lezione successiva verrà pubblicata la Knowledge Base. Si noti che la Knowledge Base è nello stato bloccato (icona di blocco).  
  
## <a name="next-step"></a>passaggio successivo  
 [Attività 9: Configurazione di un servizio dati di riferimento](../../2014/tutorials/task-9-configuring-a-reference-data-service.md)  
  
  
