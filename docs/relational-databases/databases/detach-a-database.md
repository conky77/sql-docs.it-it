---
title: Scollegare un database | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.detachdatabase.f1
helpviewer_keywords:
- database detaching [SQL Server]
- detaching databases [SQL Server]
ms.assetid: f63d4107-13e4-4bfe-922d-5e4f712e472d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35a118575be4ac15cb44588f1773ea1bb4fbc257
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68006197"
---
# <a name="detach-a-database"></a>Scollegare un database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritto come scollegare un database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. I file scollegati non vengono eliminati e possono essere ricollegati tramite CREATE DATABASE con l'opzione FOR ATTACH o FOR ATTACH_REBUILD_LOG. È possibile spostare e quindi collegare tali file in un altro server.  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per scollegare un database utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Per un elenco delle limitazioni e restrizioni, vedere [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Richiede l'appartenenza al ruolo predefinito del database db_owner.  
  
##  <a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-detach-a-database"></a>Per scollegare un database  
  
1.  In Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] connettersi all'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] e quindi espanderla.  
  
2.  Espandere **Database**e selezionare il nome del database utente che si desidera scollegare.  
  
3.  Fare clic con il pulsante destro del mouse sul nome di database, scegliere **Attività**e quindi fare clic su **Scollega**. Verrà visualizzata la finestra di dialogo **Scollega database** .  
  
     **Database da scollegare**  
     Consente di visualizzare i database da scollegare.  
  
     **Nome database**  
     Consente di visualizzare il nome del database da scollegare.  
  
     **Interrompi connessioni**  
     Consente di interrompere le connessioni al database specificato.  
  
    > [!NOTE]  
    >  Non è possibile scollegare un database con connessioni attive.  
  
     **Aggiorna statistiche**  
     Per impostazione predefinita, con l'operazione di scollegamento è possibile mantenere eventuali statistiche di ottimizzazione non aggiornate prima di scollegare il database. Per aggiornare le statistiche di ottimizzazione esistenti, fare clic su questa casella di controllo.  
  
     **Mantieni cataloghi full-text**  
     Per impostazione predefinita, con l'operazione di scollegamento è possibile mantenere eventuali cataloghi full-text associati al database. Per rimuoverli, deselezionare la casella di controllo **Mantieni cataloghi full-text** . Questa opzione è visualizzata solo quando si aggiorna un database da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
     **Status**  
     Consente di visualizzare uno degli stati seguenti: **Pronto** o **Non pronto**.  
  
     **Messaggio**  
     Nella colonna **Messaggio** possono essere visualizzate informazioni sul database simili alle seguenti:  
  
    -   Quando un database è coinvolto nella replica, lo **Stato** è **Non pronto** e nella colonna **Messaggio** viene visualizzato **Database replicato**.  
  
    -   Quando per un database esistono una o più connessioni attive, il valore di **Stato** è **Non pronto** e la colonna **Messaggio** visualizza _Connessioni attive:_ **<numero_di_connessioni_attive>** , ad esempio **Connessioni attive: 1**. Prima di poter scollegare il database è necessario disconnettere tutte le connessioni attive selezionando **Interrompi connessioni**.  
  
     Per ottenere ulteriori informazioni su un messaggio, fare clic sul testo del collegamento ipertestuale per aprire Monitoraggio attività.  
  
4.  Quando si è pronti per scollegare il database, fare clic su **OK**.  
  
> [!NOTE]  
>  Il database scollegato rimarrà visibile nel nodo **Database** di Esplora oggetti fino all'aggiornamento della vista. Per aggiornare la vista in qualsiasi momento, fare clic sul riquadro Esplora oggetti, scegliere **Vista** dalla barra dei menu e quindi **Aggiorna**.  
  
##  <a name="TsqlProcedure"></a> Con Transact-SQL  
  
#### <a name="to-detach-a-database"></a>Per scollegare un database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Nell'esempio seguente viene scollegato il database AdventureWorks2012 con skipchecks impostato su true.  
  
```  
EXEC sp_detach_db 'AdventureWorks2012', 'true';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  
