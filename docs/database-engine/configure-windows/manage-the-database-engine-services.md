---
title: Gestire il servizio Motore di database | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Configuration Manager, accessing
- Database Engine [SQL Server], services
- managing services [SQL Server], about service management
- services [SQL Server]
- SQL Server Agent service, managing
- SQL Server services, about SQL Server service
- MSSQLServer
- server configuration [SQL Server]
- managing services [SQL Server]
- SQL Server Agent service
- services [SQL Server], managing
- administering SQL Server, services
- SQL Server services
ms.assetid: aa732e43-53ba-4eea-bb9b-089da0766fc1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6ac35c702783ca5b80367c6f41af9c4c450e0be7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "67997964"
---
# <a name="manage-the-database-engine-services"></a>Gestire il servizio Motore di database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito nei sistemi operativi come servizio. Un servizio è un tipo di applicazione eseguito in background nel sistema. I servizi normalmente offrono funzionalità chiave del sistema operativo, ad esempio gestione di richieste Web, registrazione di eventi o gestione di file. I servizi possono essere eseguiti senza la visualizzazione di un'interfaccia utente sul desktop del computer. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e molti altri componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono eseguiti come servizi. Questi servizi in genere vengono avviati insieme al sistema operativo. Questo dipende dalle opzioni specificate durante l'installazione. Alcuni servizi non vengono avviati per impostazione predefinita. In questa sezione viene descritta la gestione dei vari servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Prima di accedere a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario sapere come avviare, arrestare, sospendere, riprendere e riavviare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dopo l'accesso, è possibile eseguire attività come la gestione del server o l'esecuzione di query su un database.  
  
## <a name="using-the-sql-server-service"></a>Utilizzo del servizio SQL Server  
 Quando si avvia un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], si sta avviando il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Dopo aver avviato il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , gli utenti possono creare nuove connessioni al server. Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere avviato e arrestato come servizio, in locale o in remoto. Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è definito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) se rappresenta l'istanza predefinita oppure MSSQL$ *\<nomeistanza>* se rappresenta un'istanza denominata.  
  
## <a name="using-sql-server-configuration-manager"></a>Utilizzo di Gestione configurazione SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gestione configurazione consente di arrestare, avviare o sospendere vari servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gestione configurazione non può gestire servizi di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 È inoltre possibile utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per visualizzare le proprietà del servizio selezionato. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Gestione configurazione è uno snap-in di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC). Per altre informazioni su MMC e sul funzionamento di uno snap-in, vedere la Guida di Windows.  
  
 **Per accedere a Gestione configurazione SQL Server**  
  
-   Fare clic sul menu **Start** , scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Strumenti di configurazione**e quindi **Gestione configurazione SQL Server**.  
  
 **Per accedere a Gestione configurazione SQL Server con Windows 8**  
  
 Poiché Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è uno snap-in per il programma [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console e non un programma autonomo, Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene visualizzato come applicazione durante l'esecuzione di Windows 8.0. Per aprire Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , nell'accesso alla **ricerca** , in **App**digitare **SQLServerManager12.msc** (per [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]), **SQLServerManager11.msc** (per [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) oppure **SQLServerManager10.msc** (per[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]), quindi premere **INVIO**.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|||  
|-|-|  
|[Requisiti di sicurezza per la gestione dei servizi](../../database-engine/configure-windows/security-requirements-for-managing-services.md)|[Impedire l'avvio automatico di un'istanza di SQL Server &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-prevent-automatic-startup-of-an-instance.md)|  
|[Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)|[Modificare l'account di avvio del servizio di SQL Server &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-change-the-service-startup-account.md)|  
|[Esecuzione di SQL Server in rete o non in rete](../../database-engine/configure-windows/run-sql-server-with-or-without-a-network.md)|[Configurare le opzioni di avvio del server &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)|  
|[Servizio SQL Server Browser &#40;motore di database e SSAS&#41;](../../database-engine/configure-windows/sql-server-browser-service-database-engine-and-ssas.md)|[Modificare la password degli account usati da SQL Server &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-change-the-password-of-the-accounts-used.md)|  
|[Opzioni di avvio del servizio del motore di database](../../database-engine/configure-windows/database-engine-service-startup-options.md)|[Configura log degli errori di SQL Server](../../database-engine/configure-windows/scm-services-configure-sql-server-error-logs.md)|  
|[Avviare, arrestare, sospendere, riprendere, riavviare il motore di database, SQL Server Agent o SQL Server Browser](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)|[Modifica della modalità di autenticazione del server](../../database-engine/configure-windows/change-server-authentication-mode.md)|  
|[Avvio di SQL Server in modalità utente singolo](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)|[servizio writer SQL](../../database-engine/configure-windows/sql-writer-service.md)|  
|[Avvio di SQL Server con la configurazione minima](../../database-engine/configure-windows/start-sql-server-with-minimal-configuration.md)|[Trasmettere un messaggio di arresto &#40;prompt dei comandi&#41;](../../database-engine/configure-windows/broadcast-a-shutdown-message-command-prompt.md)|  
|[Connettersi a un altro computer &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-connect-to-another-computer.md)|[Accedere a un'istanza di SQL Server &#40;prompt dei comandi&#41;](../../database-engine/configure-windows/log-in-to-an-instance-of-sql-server-command-prompt.md)|  
|[Impostare un'istanza di SQL Server per l'avvio automatico &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-set-an-instance-to-start-automatically.md)|[Configurare le autorizzazioni del file system per l'accesso al motore di database](../../database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
 [Configurazione di SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md)  
  
 [Accesso a SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
  
