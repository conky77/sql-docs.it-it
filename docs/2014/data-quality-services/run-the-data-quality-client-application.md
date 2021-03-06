---
title: Eseguire l'applicazione Data Quality Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bbb790fc5067d1544cd4b3d9d6e90b34be8e2b77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484146"
---
# <a name="run-the-data-quality-client-application"></a>Eseguire l'applicazione client Data Quality
  È possibile utilizzare [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) eseguendo il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] e accedendo a un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
 È necessario aver completato l'installazione di [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] tramite l'esecuzione del file DQSInstaller.exe. Per altre informazioni, vedere [Eseguire DQSInstaller.exe per completare l'installazione del server DQS](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per potere accedere al [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], è necessario disporre di uno dei tre ruoli DQS (dqs_adminstrator, dqs_kb_editor o dqs_kb_operator) concessi per il database DQS_MAIN.  
  
##  <a name="Run"></a>Esegui Data Quality Client  
 Per eseguire il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] nel computer in cui è stato installato, procedere come segue:  
  
1.  Fare clic su **Start**, puntare **Tutti i programmi**, fare clic su **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, su **Data Quality Services**, quindi su **Client Data Quality**.  
  
2.  Nella finestra di dialogo **Connetti al server** :  
  
    1.  Specificare il server a cui si desidera connettere l'applicazione [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Selezionare **(LOCAL)** per connettersi al [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] nel computer locale. È anche possibile fare clic sulla freccia verso il basso e selezionare ** \<Esplora rete per altri server>** per connettersi a un server diverso (o per connettersi al server locale in base al nome). Verrà visualizzata la finestra di dialogo **Cerca server** . È possibile selezionare un server nella scheda **Server locali** o nella scheda **Server di rete** .  
  
    2.  Se si desidera crittografare il trasferimento dei dati tra il [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] e il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], fare clic su **Opzioni** e quindi selezionare la casella di controllo **Crittografa connessione**.  
  
3.  Fare clic su **Connetti**.  
  
 Verrà visualizzata la schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Per altre informazioni, vedere [Schermata iniziale del client Data Quality](../../2014/data-quality-services/data-quality-client-home-screen.md).  
  
  
