---
title: Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- Distributors [SQL Server replication], modifying
- modifying replication properties, Distributors
- Distributors [SQL Server replication], properties
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e4049cfa36020431e9cae8cbe2431c1c270d5deb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68212021"
---
# <a name="view-and-modify-distributor-and-publisher-properties"></a>Visualizzazione e modifica delle proprietà del server di pubblicazione e del database di distribuzione
  In questo argomento viene descritto come visualizzare e modificare le proprietà del database di distribuzione e del server di pubblicazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o RMO (Replication Management Objects).  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare e modificare le proprietà di server di pubblicazione e database di distribuzione, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Raccomandazioni  
  
-   Per i server di pubblicazione che eseguono versioni precedenti a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], un utente nel ruolo predefinito del server **sysadmin** può registrare i Sottoscrittori nella pagina **Sottoscrittori**. A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]non è più necessario registrare esplicitamente i Sottoscrittori per la replica.  
  
###  <a name="Security"></a> Sicurezza  
 Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione.  
  
##  <a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-view-and-modify-distributor-properties"></a>Per visualizzare e modificare le proprietà del database di distribuzione  
  
1.  Connettersi al database di distribuzione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi espandere il nodo del server.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Replica** e quindi scegliere **Proprietà server di distribuzione**.  
  
3.  Visualizzare e modificare le proprietà nella finestra di dialogo **Proprietà database di distribuzione - \<DatabaseDistribuzione>** .  
  
    -   Per visualizzare e modificare le proprietà di un database di distribuzione, fare clic sul pulsante delle proprietà ( **...** ) relativo al database nella pagina **Generale** della finestra di dialogo.  
  
    -   Per visualizzare e modificare le proprietà del server di pubblicazione associato al database di distribuzione, fare clic sul pulsante delle proprietà ( **...** ) relativo al server di pubblicazione nella pagina **Server di pubblicazione** della finestra di dialogo.  
  
    -   Per accedere ai profili degli agenti di replica, fare clic sul pulsante **Impostazioni predefinite profili** nella pagina **Generale** della finestra di dialogo. Per altre informazioni, vedere [Replication Agent Profiles](agents/replication-agent-profiles.md).  
  
    -   Per modificare la password dell'account utilizzato quando stored procedure di amministrazione vengono eseguite sul server di pubblicazione e aggiornano le informazioni sul server di distribuzione, immettere una nuova password nelle caselle **Password** e **Conferma password** della pagina **Server di pubblicazione** della finestra di dialogo. Per altre informazioni, vedere [Sicurezza del database di distribuzione](security/secure-the-distributor.md).  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
#### <a name="to-view-and-modify-publisher-properties"></a>Per visualizzare e modificare le proprietà del server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Replica** e quindi scegliere **Proprietà server di pubblicazione**.  
  
3.  Visualizzare e modificare le proprietà nella finestra di dialogo **Proprietà server di pubblicazione- \< >server di pubblicazione** .  
  
    -   Un utente nel ruolo predefinito del server **sysadmin** può abilitare i database per la replica nella pagina **Database di pubblicazione** . L'abilitazione di un database non ne comporta la pubblicazione, ma piuttosto consente a un utente nel ruolo predefinito del database **db_owner** per il database in questione di creare una o più pubblicazioni nel database.  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Con Transact-SQL  
 È possibile visualizzare le proprietà del server di pubblicazione e del database di distribuzione a livello di programmazione utilizzando le stored procedure di replica.  
  
#### <a name="to-view-distributor-and-distribution-database-properties"></a>Per visualizzare le proprietà del database di distribuzione  
  
1.  Eseguire [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) per restituire informazioni sul server di distribuzione, il database di distribuzione e la directory di lavoro.  
  
2.  Eseguire [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) per restituire le proprietà di un database di distribuzione specificato.  
  
#### <a name="to-change-distributor-and-distribution-database-properties"></a>Per modificare le proprietà del server di distribuzione e del database di distribuzione  
  
1.  Nel server di distribuzione eseguire [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) per modificare le proprietà del server di distribuzione.  
  
2.  Nel server di distribuzione eseguire [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) per modificare le proprietà del database di distribuzione.  
  
3.  Nel database di distribuzione eseguire [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) per modificare la password del database di distribuzione.  
  
    > [!IMPORTANT]  
    >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file di script, proteggere tale file per impedire l'accesso non autorizzato.  
  
4.  Nel database di distribuzione eseguire [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) per modificare le proprietà di un server di pubblicazione utilizzando il database di distribuzione.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] di esempio riportato di seguito restituisce informazioni sul database di distribuzione e sul database di distribuzione.  
  
 [!code-sql[HowTo#sp_helpdistributor](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributor)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributiondb)]  
  
 In questo esempio vengono modificati i periodi di memorizzazione per il server di distribuzione, la password utilizzata per la connessione al server di distribuzione e l'intervallo con cui il server di distribuzione verifica lo stato di diversi agenti di replica, noto anche come intervallo di heartbeat.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file di script, proteggere tale file per impedire l'accesso non autorizzato.  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_property)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributiondb)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_password)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
  
#### <a name="to-view-and-modify-distributor-properties"></a>Per visualizzare e modificare le proprietà del database di distribuzione  
  
1.  Creare una connessione al server di distribuzione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Passare l'oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection> indicato nel passaggio 1.  
  
3.  (Facoltativo) Controllare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> per verificare che il server attualmente connesso sia un server di distribuzione.  
  
4.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> per ottenere le proprietà dal server.  
  
5.  (Facoltativo) Per modificare le proprietà, specificare un nuovo valore per una o più proprietà del server di distribuzione che è possibile impostare sull'oggetto <xref:Microsoft.SqlServer.Replication.ReplicationServer> .  
  
6.  (Facoltativo) Se la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> sull'oggetto <xref:Microsoft.SqlServer.Replication.ReplicationServer> è impostata su `true`, chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server.  
  
#### <a name="to-view-and-modify-distribution-database-properties"></a>Per visualizzare e modificare le proprietà del database di distribuzione  
  
1.  Creare una connessione al server di distribuzione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.DistributionDatabase>. Specificare la proprietà relativa al nome e passare l'oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection> indicato nel passaggio 1.  
  
3.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> per ottenere le proprietà dal server. Se il metodo restituisce `false`, il database con il nome specificato non esiste nel server.  
  
4.  (Facoltativo) Per modificare le proprietà, specificare un nuovo valore per una delle proprietà dell'oggetto <xref:Microsoft.SqlServer.Replication.DistributionDatabase> che è possibile impostare.  
  
5.  (Facoltativo) Se la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> sull'oggetto <xref:Microsoft.SqlServer.Replication.DistributionDatabase> è impostata su `true`, chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server.  
  
#### <a name="to-view-and-modify-publisher-properties"></a>Per visualizzare e modificare le proprietà del server di pubblicazione  
  
1.  Creare una connessione al server di pubblicazione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.DistributionPublisher>. Specificare la proprietà <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> e passare l'oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection> indicato nel passaggio 1.  
  
3.  (Facoltativo) Per modificare le proprietà, specificare un nuovo valore per una delle proprietà dell'oggetto <xref:Microsoft.SqlServer.Replication.DistributionPublisher> che è possibile impostare.  
  
4.  (Facoltativo) Se la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> sull'oggetto <xref:Microsoft.SqlServer.Replication.DistributionPublisher> è impostata su `true`, chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server.  
  
#### <a name="to-change-the-password-for-the-administrative-connection-from-the-publisher-to-the-distributor"></a>Per modificare la password per la connessione amministrativa dal server di pubblicazione al database di distribuzione  
  
1.  Creare una connessione al server di distribuzione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.ReplicationServer>.  
  
3.  Impostare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> sulla connessione creata nel passaggio 1.  
  
4.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> per recuperare le proprietà dell'oggetto.  
  
5.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> . Passare il nuovo valore della password per il parametro *password* .  
  
    > [!IMPORTANT]  
    >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](https://go.microsoft.com/fwlink/?LinkId=34733) offerti da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
6.  (Facoltativo) Eseguire i passaggi seguenti per modificare la password in ogni server di pubblicazione remoto che utilizza questo server di distribuzione:  
  
    1.  Creare una connessione al server di pubblicazione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
    2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.ReplicationServer>.  
  
    3.  Impostare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> sulla connessione creata nel passaggio 6a.  
  
    4.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> per recuperare le proprietà dell'oggetto.  
  
    5.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> . Passare il nuovo valore della password indicato nel passaggio 5 per il parametro *password* .  
  
###  <a name="PShellExample"></a> Esempio (RMO)  
 In questo esempio viene illustrato come modificare le proprietà del database di distribuzione e del database di distribuzione.  
  
> [!IMPORTANT]  
>  Per evitare di archiviare le credenziali del codice, la nuova password del server di distribuzione viene specificata in fase di esecuzione.  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## <a name="see-also"></a>Vedere anche  
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Disabilitare la pubblicazione e la distribuzione](disable-publishing-and-distribution.md)   
 [Configura distribuzione](configure-distribution.md)   
 [Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md)   
 [Script di informazioni su database di distribuzione e server di pubblicazione](administration/distributor-and-publisher-information-script.md)   
 [Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md)   
 [Visualizzazione delle informazioni ed esecuzione di attività tramite Monitoraggio replica](monitor/view-information-and-perform-tasks-replication-monitor.md)  
  
  
