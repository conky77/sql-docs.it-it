---
title: Registra database con mirroring | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.registermirroreddb.f1
ms.assetid: 6acd02b9-2311-49b0-a5f8-3852beecb4b0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b5be7eb52d0aa8c0a94b1a4ff63493e7f641bdbd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754459"
---
# <a name="register-mirrored-database"></a>Registra database con mirroring
  Utilizzare questa finestra di dialogo per registrare uno o più database con mirroring su una determinata istanza del server aggiungendo il database o i database a Monitoraggio mirroring del database. Quando viene aggiunto un database, Monitoraggio mirroring del database memorizza nella cache le informazioni relative al database, ai suoi partner e alla modalità di connessione a questi ultimi.  
  
> [!IMPORTANT]  
>  Gli utenti membri del ruolo predefinito del server **sysadmin** nell'istanza del server principale ma non nell'istanza del server mirror potranno visualizzare lo stato solo nell'istanza del server principale.  
  
 **Per utilizzare SQL Server Management Studio per il monitoraggio del mirroring del database**  
  
-   [Avviare il monitoraggio mirroring del database &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a>Opzioni  
 **Istanza del server**  
 Selezionare un'istanza del server dall'elenco che contiene le istanze del server per le quali Monitoraggio mirroring del database ha già archiviato una connessione oppure fare clic su **Connetti**. Per specificare nuove credenziali per un'istanza del server inclusa nell'elenco, fare clic su **Connetti** e stabilire la connessione usando le nuove credenziali.  
  
> [!NOTE]  
>  Per registrare i database in più istanze del server, dopo aver terminato il controllo dei database desiderati per un'istanza del server, fare clic su **Applica**, quindi selezionare un'altra istanza del server.  
  
 **Connettere**  
 Per specificare nuove credenziali per l'istanza del server, fare clic su **Connetti** e stabilire la connessione usando le nuove credenziali. Durante la connessione a un'istanza del server, Monitoraggio mirroring del database visualizza il messaggio **In attesa di dati**.  
  
 **Database con mirroring**  
 La griglia **Database con mirroring** elenca i database con mirroring nell'istanza del server.  
  
 La griglia include le colonne seguenti:  
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|**Registra**|Consente di controllare ogni database da registrare. Se un database è attualmente monitorato, la relativa casella di controllo è selezionata e disabilitata.<br /><br /> Nota: per annullare la registrazione di un database, chiudere la finestra di dialogo **Registra database con mirroring** , selezionare il database nell'albero di navigazione e scegliere **Annulla registrazione** dal menu **Azione** .|  
|**Database**|Nome di un database con mirroring sull'istanza del server selezionata.|  
|**Ruolo corrente**|Ruolo del mirroring corrente del database, Principale o Mirror, sull'istanza del server selezionata.|  
|**Partner (Connetti come)**|Nome del partner di failover per il database. **Autenticazione di Windows dell'utente della console** o **Autenticazione di SQL Server di '***\<nome account di accesso>***'** sono le stringhe visualizzate tra parentesi. Si tratta delle informazioni di autenticazione attualmente utilizzate, se l'istanza è stata aggiunta in precedenza, o che verranno utilizzate se l'istanza non è stata aggiunta al monitoraggio.|  
  
 **Quando viene scelto OK visualizza la finestra di dialogo Gestione connessioni a istanze server.**  
 Per impostazione predefinita, Monitoraggio mirroring del database utilizza le credenziali per l'autenticazione di Windows per le istanze del server partner per le quali le credenziali non siano state specificate in precedenza. Abilitare l'opzione per modificare le credenziali per una o più istanze del server al termine della registrazione dei database.  
  
 Se l'opzione è abilitata, quando si fa clic su **OK**viene visualizzata la finestra di dialogo **Gestione connessioni server** . nella quale è possibile scegliere un'istanza del server per la quale specificare le credenziali da utilizzare nel monitoraggio per la connessione a un determinato partner di failover.  
  
 Per modificare le credenziali per un partner, trovare la relativa voce nella griglia **Istanze server** e fare clic su **Modifica** nella riga corrispondente. Viene visualizzata la finestra di dialogo **Connetti al server** per il nome dell'istanza del server specificata, con i controlli delle credenziali inizializzati sul valore attualmente memorizzato nella cache. Modificare le credenziali in base alle necessità e fare clic su **Connetti**. Se le credenziali hanno privilegi sufficienti, la colonna **Connetti tramite** viene aggiornata con le nuove credenziali.  
  
 **Applica**  
 Fare clic sul pulsante per registrare i database selezionati e salvare le credenziali per le istanze del server partner, mantenendo aperta la finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare il monitoraggio mirroring del database &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Monitoraggio del mirroring del database &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Avvio della Configurazione guidata sicurezza mirroring del database &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
