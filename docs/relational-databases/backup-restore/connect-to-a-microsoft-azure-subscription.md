---
title: Connettersi a una sottoscrizione di Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cca5a270-643f-4677-8802-98464f19f82a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 765763ae01183d0907e5371cf1420205cd5737b5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68076128"
---
# <a name="connect-to-a-microsoft-azure-subscription"></a>Connettersi a una sottoscrizione di Microsoft Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Usare **Connettersi a una sottoscrizione di Microsoft Azure** per registrare un contenitore BLOB di Azure esistente con l'istanza di SQL Server.  Nella finestra di dialogo verrà creata una firma di accesso condiviso e un criterio di accesso condiviso in un contenitore BLOB di Azure, quindi verranno create le credenziali di SQL Server.  Questa finestra di dialogo viene visualizzata quando si usa l'attività Backup o Ripristina di SQL Server Management Studio e l'operazione implica un dispositivo URL.

## <a name="limitation"></a>Limitazione
**Connettersi a una sottoscrizione di Microsoft Azure** funzionerà solo con un account di archiviazione di Microsoft Azure creato tramite il modello di distribuzione di Gestione dei servizi (classica).  Per altre informazioni sui modelli di distribuzione di Microsoft Azure, vedere [Confronto tra distribuzione di Azure Resource Manager e classica](https://azure.microsoft.com/documentation/articles/resource-manager-deployment-model/).

## <a name="options"></a>Opzioni
**Accedi**     
Accedere con l'account Azure appropriato.

**Selezionare la sottoscrizione da usare**      
Selezionare la sottoscrizione desiderata dall'elenco a discesa.

**Selezionare l'account di archiviazione**  
Selezionare l'account di archiviazione desiderato dall'elenco a discesa.

**Selezionare il contenitore BLOB**   
Selezionare il contenitore BLOB desiderato dall'elenco a discesa.

**Scadenza criteri di accesso condiviso**   
I criteri di accesso condiviso scadranno alla data indicata.  La data di scadenza predefinita è un anno dalla creazione.  Modificare come desiderato.

**Firma di accesso condiviso generata**   
Nella casella di testo con formattazione verrà visualizzata la firma di accesso condiviso creata.

**Crea credenziali**   
Il pulsante genererà i criteri di accesso condiviso e una firma di accesso condiviso, quindi creerà le credenziali di SQL Server.
