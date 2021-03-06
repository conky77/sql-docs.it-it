---
title: Configurare le autorizzazioni del file system per l'accesso al motore di database | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a42a4a17a1eee9222318e2b508b28d190361d85e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68012786"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>Configurare le autorizzazioni del file system per l'accesso al motore di database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene illustrato come concedere al [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]l'accesso al file system nel percorso in cui sono archiviati i file di database. Il servizio [!INCLUDE[ssDE](../../includes/ssde-md.md)] deve disporre dell'autorizzazione del file system di Windows per accedere alla cartella file in cui sono archiviati i file di database. L'autorizzazione per il percorso predefinito viene configurata durante l'installazione. Se si posizionano i file di database in un percorso diverso, potrebbe essere necessario seguire questi passaggi per concedere al [!INCLUDE[ssDE](../../includes/ssde-md.md)] l'autorizzazione di controllo completo per il percorso in questione.  
  
 A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] le autorizzazioni vengono assegnate al SID per servizio per ognuno dei relativi servizi. Tramite questo sistema viene fornito un livello elevato di isolamento e protezione del servizio. Il SID per servizio deriva dal nome del servizio ed è univoco per ogni servizio. L'argomento [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) descrive il SID per servizio e nella sezione **Privilegi e diritti di Windows**specifica i nomi. Si tratta del SID per servizio a cui deve essere assegnata l'autorizzazione di accesso per il percorso del file.  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>Per concedere le autorizzazioni del file system al SID per servizio  
  
1.  Utilizzando Esplora risorse passare al percorso del file system in cui sono archiviati i file di database. Fare clic con il pulsante destro del mouse sulla cartella del file system e quindi scegliere **Proprietà**.  
  
2.  Nella scheda **Sicurezza** fare clic su **Modifica**quindi su **Aggiungi**.  
  
3.  Nella finestra di dialogo per la **selezione di utenti, computer, account del servizio o gruppi** fare clic su **Percorsi**sopra l'elenco di percorsi, selezionare il nome del computer e quindi fare clic su **OK**.  
  
4.  Nella casella **Immettere i nomi degli oggetti da selezionare** digitare il nome del SID per servizio elencato nell'argomento [**Configurare account di servizio e autorizzazioni di Windows**](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)della documentazione online. Come nome SID per servizio del [!INCLUDE[ssDE](../../includes/ssde-md.md)] usare **NT SERVICE\MSSQLSERVER** per un'istanza predefinita o **NT SERVICE\MSSQL$InstanceName** per un'istanza denominata.  
  
5.  Fare clic su **Controlla nomi** per convalidare la voce. Se la convalida ha esito negativo, potrebbe indicare che il nome non è stato trovato. Quando si fa clic su **OK**, viene visualizzata la finestra di dialogo **Trovati più nomi** . A questo punto selezionare il nome SID per servizio, **MSSQLSERVER** o **NT SERVICE\MSSQL$InstanceName**, quindi fare clic su **OK**.  Fare di nuovo clic su **OK** per tornare alla finestra di dialogo **Autorizzazioni** .   
6.  Nella casella di nomi **Gruppo o utente** selezionare il SID per servizio e quindi nella casella **Autorizzazioni per** \<nome> selezionare la casella di controllo **Consenti** per **Controllo completo**.  
  
7. Fare clic su **Applica**quindi due volte su **OK** per uscire.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire il servizio Motore di database](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [Spostare i database di sistema](../../relational-databases/databases/move-system-databases.md)   
 [Spostare database utente](../../relational-databases/databases/move-user-databases.md)  
  
  
