---
title: Visualizzare file di log offline | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, viewing offline logs
- offline log files
ms.assetid: 9223e474-f224-4907-a4f2-081e11db58f5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5547d5fb1c2b083a51837df5d9cacb1be393f555
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63144597"
---
# <a name="view-offline-log-files"></a>Visualizzare file di log offline
  A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], è possibile visualizzare file di log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un'istanza locale o remota di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando l'istanza di destinazione è offline o non può essere avviata.  
  
 È possibile accedere ai file di log offline tramite lo strumento Server registrati o a livello di codice tramite query WMI e WQL (WMI Query Language).  
  
> [!NOTE]  
>  È possibile utilizzare questi metodi anche per connettersi a un'istanza a cui, benché online, non è possibile connettersi tramite una connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per qualche motivo.  
  
## <a name="before-you-begin"></a>Operazioni preliminari  
 Per connettersi ai file di log offline, è necessario che nel computer utilizzato per visualizzare i file di log offline e nel computer in cui si trovano i file di log che si desidera visualizzare sia installata un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se in entrambi i computer è installata un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è possibile visualizzare file offline per istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e per istanze che eseguono versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uno dei computer.  
  
 Se si usa Server registrati, l'istanza a cui ci si vuole connettere deve essere registrata in **Gruppi di server locali** o **Server di gestione centrale**. L'istanza può essere registrata in modo autonomo o essere un membro di un gruppo di server. Per ulteriori informazioni su come aggiungere un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a Server registrati, vedere gli argomenti seguenti:  
  
-   [Creare o modificare un gruppo di server &#40;SQL Server Management Studio&#41;](../../ssms/register-servers/create-or-edit-a-server-group-sql-server-management-studio.md)  
  
-   [Registrare un server connesso &#40;SQL Server Management Studio&#41;](../../ssms/register-servers/register-a-connected-server-sql-server-management-studio.md)  
  
-   [Creare un server di gestione centrale e un gruppo di server &#40;SQL Server Management Studio&#41;](../../ssms/register-servers/create-a-central-management-server-and-server-group.md)  
  
 Per ulteriori informazioni su come visualizzare file di log offline a livello di codice tramite query WMI e WQL, vedere gli argomenti seguenti:  
  
-   [Classe SqlErrorLogEvent](../wmi-provider-configuration-classes/sqlerrorlogevent-class.md) Questo argomento mostra come recuperare i valori per gli eventi registrati in un file di log specificato.  
  
-   [SqlErrorLogFile Class](../wmi-provider-configuration-classes/sqlerrorlogfile-class.md) Questo argomento mostra come recuperare le informazioni su tutti i file di log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Autorizzazioni  
 Per connettersi a un file di log offline, è necessario disporre delle autorizzazioni seguenti nei computer locale e remoto:  
  
-   Accesso in lettura allo spazio dei nomi WMI **Root\Microsoft\SqlServer\ComputerManagement12** . Per impostazione predefinita, chiunque dispone di accesso in lettura tramite l'autorizzazione Abilita account. Per ulteriori informazioni, vedere la procedura "Per verificare le autorizzazioni WMI" più avanti in questa sezione.  
  
-   Autorizzazione di lettura per la cartella che contiene i file di log degli errori. Per impostazione predefinita, i file di log degli errori si trovano nel percorso seguente, dove \<*Unità>* rappresenta l'unità in cui è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e \<*NomeIstanza*> è il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
     **\<Unità>: \Programmi\microsoft SQL Server\MSSQL12. \<NomeIstanza> \Mssql\Log**  
  
 Per verificare le impostazioni di sicurezza dello spazio dei nomi WMI, è possibile utilizzare lo snap-in Controllo WMI.  
  
#### <a name="to-verify-wmi-permissions"></a>Per verificare le autorizzazioni WMI  
  
1.  Aprire lo snap-in Controllo WMI. A tale scopo, effettuare una delle operazioni seguenti a seconda del sistema operativo in uso:  
  
    -   Fare **** clic su Start `wmimgmt.msc` , digitare nella casella **Inizia ricerca** , quindi premere INVIO.  
  
    -   Fare clic sul pulsante **Start**, scegliere `wmimgmt.msc` **Esegui**, digitare e quindi premere INVIO.  
  
2.  Per impostazione predefinita, lo snap-in Controllo WMI gestisce il computer locale.  
  
     Se si desidera connettersi a un computer remoto, effettuare le operazioni seguenti:  
  
    1.  Fare clic con il pulsante destro del mouse su **Controllo WMI (computer locale)** , quindi scegliere **Connetti a un altro computer**.  
  
    2.  Nella finestra di dialogo **Cambio computer gestito** fare clic su **Altro computer**.  
  
    3.  Immettere il nome del computer remoto, quindi fare clic su **OK**.  
  
3.  Fare clic con il pulsante destro del mouse su **controllo WMI (locale)** o **controllo WMI (***NomeComputerRemoto***)**, quindi scegliere **Proprietà**.  
  
4.  Nella finestra di dialogo delle proprietà di **Controllo WMI** fare clic sulla scheda **Sicurezza** .  
  
5.  Nell'albero dello spazio dei nomi individuare e selezionare lo spazio dei nomi seguente:  
  
     **Root\Microsoft\SqlServer\ComputerManagement10**  
  
6.  Fare clic su **Security**.  
  
7.  Verificare che l'account usato abbia l'autorizzazione **Abilita account** . Questa autorizzazione consente accesso in lettura a oggetti WMI.  
  
### <a name="view-log-files"></a>Visualizzare file di log  
 Nella procedura seguente viene illustrato come visualizzare file di log offline tramite Server registrati. Nella procedura si suppone quanto segue:  
  
 L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui si desidera connettersi è già registrata in Server registrati.  
  
##### <a name="to-view-log-files-for-instances-that-are-offline"></a>Per visualizzare file di log per istanze offline  
  
1.  Se si desidera visualizzare file di log offline in un'istanza locale, assicurarsi di avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] con autorizzazioni elevate. A questo scopo, quando si avvia [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], fare clic con il pulsante destro del mouse su **SQL Server Management Studio**, quindi scegliere **Esegui come amministratore**.  
  
2.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]scegliere **Server registrati** dal menu **Visualizza**.  
  
3.  Nell'albero della console individuare l'istanza in cui si desidera visualizzare i file offline.  
  
4.  Eseguire una delle operazioni seguenti:  
  
    -   Se l'istanza è in **Gruppi di server locali**, espandere **Gruppi di server locali**, espandere il gruppo di server se l'istanza è un membro di un gruppo, fare clic con il pulsante destro del mouse sull'istanza e quindi scegliere **Visualizza log di SQL Server**.  
  
    -   Se l'istanza corrisponde allo stesso server di gestione centrale, espandere **Server di gestione centrale**, fare clic con il pulsante destro del mouse sull'istanza, scegliere **Azioni server di gestione centrale**, quindi fare clic su **Visualizza log di SQL Server**.  
  
    -   Se l'istanza è in **Server di gestione centrale**, espandere **Server di gestione centrale**, espandere il server di gestione centrale, fare clic con il pulsante destro del mouse sull'istanza o espandere un gruppo di server e fare clic con il pulsante destro del mouse sull'istanza, quindi scegliere **Visualizza log di SQL Server**.  
  
5.  Se ci si connette a un'istanza locale, la connessione viene eseguita utilizzando le credenziali utente correnti.  
  
     Se ci si connette a un'istanza remota, nella finestra di dialogo **Visualizzatore file di log - Connetti come** eseguire una di queste operazioni:  
  
    -   Per connettersi come utente corrente, verificare che la casella di controllo **Connetti come altro utente** sia deselezionata, quindi fare clic su **OK**.  
  
    -   Per connettersi come utente diverso, selezionare la casella di controllo **Connetti come altro utente** , quindi fare clic su **Imposta utente**. Quando viene richiesto, immettere le credenziali utente con il nome utente in formato *nome_dominio*\\*nome_utente*, fare clic su **OK**e quindi di nuovo su **OK** per connettersi.  
  
    > [!NOTE]  
    >  Se il caricamento dei file di log richiede troppo tempo, è possibile fare clic su **Arresta** nella barra degli strumenti Visualizzatore file di log.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzatore file di log](log-file-viewer.md)  
  
  
