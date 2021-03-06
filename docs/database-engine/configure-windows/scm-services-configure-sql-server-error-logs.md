---
title: Configurare log degli errori di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8e746861ef30305a901c388f7574a4a27e2edab4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "74127485"
---
# <a name="scm-services---configure-sql-server-error-logs"></a>Gestione configurazione SQL Server - Configurare log degli errori di SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritto come visualizzare o modificare la modalità di riciclo dei log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Per aprire la finestra di dialogo Configura log degli errori di SQL Server  

1. In Esplora oggetti espandere l'istanza di SQL Server, espandere **Gestione**, fare clic con il pulsante destro del mouse su **Log di SQL Server**e quindi scegliere **Configura**.

2. Nella finestra di dialogo **Configura log degli errori di SQL Server** , scegliere dalle opzioni seguenti.

    a. Conteggio file di log

      **Limita il numero di file di log degli errori creati prima di essere riciclati**

      Selezionare questa opzione per limitare il numero di log degli errori creati prima di essere riciclati. Ogni volta che viene avviata un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene creato un nuovo log degli errori. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mantiene backup dei sei log precedenti, a meno che non si selezioni questa opzione e non si specifichi un diverso numero massimo di log degli errori tramite l'opzione seguente.  
  
      **Numero massimo di file di log degli errori**

      Specificare il numero massimo di file di log degli errori archiviati creati prima che vengano riciclati. Il valore predefinito è 6, escluso quello corrente. Questo valore determina il numero di log di backup precedenti conservati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima del riciclo.

    b. Dimensioni file di log

      **Dimensioni massime del file di log degli errori in KB**

      È possibile impostare le dimensioni per ogni file in KB. Se si lascia 0, le dimensioni del log sono illimitate.
