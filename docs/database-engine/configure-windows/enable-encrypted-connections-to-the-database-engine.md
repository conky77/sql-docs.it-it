---
title: Abilitazione di connessioni crittografate al Motore di database | Microsoft Docs
ms.custom: ''
ms.date: 08/29/2019
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- TLS [SQL Server]
- Transport Layer Security (TLS)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
- TLS certificates
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 53ca4d2631e41e0a815dbf240fc0a7006ec8ce8b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "75252854"
---
# <a name="enable-encrypted-connections-to-the-database-engine"></a>Abilitazione di connessioni crittografate al Motore di database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  In questo argomento viene descritto come abilitare connessioni crittografate per un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] specificando un certificato per il [!INCLUDE[ssDE](../../includes/ssde-md.md)] tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . È necessario che sia disponibile un certificato per il computer server e che il computer client sia impostato per considerare attendibile l'autorità radice del certificato. Il processo di provisioning consiste nell'installazione di un certificato tramite l'importazione in Windows.  
  
> [!IMPORTANT]
> A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], Secure Sockets Layer (SSL) non è più disponibile. Usare in alternativa Transport Layer Security (TLS).

## <a name="transport-layer-security-tls"></a>Transport Layer Security (TLS)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può usare Transport Layer Security (TLS) per crittografare i dati trasmessi attraverso una rete tra un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un'applicazione client. La crittografia TLS viene eseguita a livello di protocollo ed è disponibile per tutti i client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supportati.
È possibile usare TLS per la convalida del server quando è necessaria la crittografia per una connessione client. Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione in un computer a cui è stato assegnato un certificato da un'autorità di certificazione pubblica, l'identità del computer e dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene garantita dalla catena di certificati che fanno riferimento all'autorità radice attendibile. In questo caso per la convalida del server è necessario che il computer in cui viene eseguita l'applicazione client sia configurato in modo da considerare attendibile l'autorità radice del certificato usato dal server. È anche possibile usare la crittografia con un certificato autofirmato, come descritto nella sezione successiva, sebbene un certificato autofirmato offra un livello di protezione limitato.
Il livello di crittografia usato da TLS, a 40 bit o a 128 bit, varia a seconda della versione del sistema operativo Microsoft Windows in esecuzione nei computer delle applicazioni e dei database.

> [!WARNING]
> L'uso del livello di crittografia a 40 bit non è considerato sicuro.

> [!WARNING]
> Le connessioni TLS crittografate con un certificato autofirmato non offrono un livello di sicurezza elevato. Sono infatti suscettibili ad attacchi man-in-the-middle. Non è consigliabile affidarsi a TLS usando certificati autofirmati in un ambiente di produzione o su server connessi a Internet.

L'abilitazione della crittografia TLS contribuisce alla sicurezza del traffico di dati in rete tra le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e le applicazioni. Tuttavia, quando tutto il traffico tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un'applicazione client è crittografato con TLS, sono necessarie le operazioni di elaborazione aggiuntive seguenti:
-  Al momento della connessione è necessario un ulteriore round trip in rete.
-  I pacchetti inviati dall'applicazione all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere crittografati dallo stack TLS del client e decrittografati dallo stack TLS del server.
-  I pacchetti inviati dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'applicazione devono essere crittografati dallo stack TLS del server e decrittografati dallo stack TLS del client.

## <a name="remarks"></a>Osservazioni
 Il certificato deve essere emesso per l'opzione **Autenticazione server**. Il nome del certificato deve essere il nome di dominio completo (FQDN) del computer.  
  
 I certificati per gli utenti vengono archiviati nel computer locale. Per installare un certificato per l'uso da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario eseguire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager con un account che dispone di privilegi di amministratore locale.

 Il client deve essere in grado di verificare la proprietà del certificato utilizzato dal server. Se il client dispone del certificato chiave pubblica dell'autorità di certificazione che ha firmato il certificato del server, non sono necessarie ulteriori operazioni di configurazione. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sono inclusi i certificati chiave pubblica di numerose autorità di certificazione. Se il certificato del server è stato firmato da un'autorità di certificazione pubblica o privata per la quale il client non dispone del certificato chiave pubblica, è necessario installare il certificato chiave pubblica dell'autorità di certificazione che ha firmato il certificato del server.  
  
> [!NOTE]  
> Per utilizzare la crittografia in un cluster di failover, è necessario installare il certificato server con il nome DNS completo del server virtuale in tutti i nodi del cluster di failover. Se ad esempio si dispone di un cluster costituito da due nodi, denominati rispettivamente ***test1.\*\<nomeazienda>\*.com*** e ***test2.\*\<nomeazienda>\*.com***, e di un server virtuale denominato ***virtsql***, è necessario installare un certificato per ***virtsql.\*\<nomeazienda>\*.com*** in entrambi i nodi. È possibile impostare il valore dell'opzione **ForceEncryption** nella casella della proprietà **Protocolli per virtsql** di **Configurazione di rete SQL Server** su **Sì**.

> [!NOTE]
> Se si creano connessioni crittografate per un indicizzatore di Ricerca di Azure a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale di Azure, vedere [Configurare una connessione da un indicizzatore di Ricerca di Azure a SQL Server in una VM Azure](https://azure.microsoft.com/documentation/articles/search-howto-connecting-azure-sql-iaas-to-azure-search-using-indexers/). 

## <a name="certificate-requirements"></a>Requisiti per i certificati
Affinché un certificato TLS venga caricato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario che vengano soddisfatte le condizioni seguenti:

- Il certificato deve essere presente nell'archivio certificati del computer locale oppure nell'archivio certificati dell'utente corrente.

- L'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve avere l'autorizzazione necessaria per accedere al certificato TLS.

- L'ora di sistema corrente deve essere successiva al valore della proprietà **Valido dal** del certificato e antecedente al valore della proprietà Valido fino a del certificato.

- Il certificato deve essere destinato all'autenticazione del server. Per questa operazione è necessario impostare la proprietà **Utilizzo chiavi avanzato** del certificato su **Autenticazione server (1.3.6.1.5.5.7.3.1)** .

- Il certificato deve essere creato tramite l'opzione **KeySpec** **AT_KEYEXCHANGE**. In genere, la proprietà del certificato relativa all'utilizzo della chiave (**KEY_USAGE**) include anche la crittografia della chiave (**CERT_KEY_ENCIPHERMENT_KEY_USAGE**).

- La proprietà **Soggetto** del certificato deve specificare che il nome comune (CN, Common Name) corrisponde al nome host oppure al nome di dominio completo (FQDN, Fully Qualified Domain Name) del server. Quando si usa il nome host, nel certificato deve essere specificato il suffisso DNS. Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione in un cluster di failover, è necessario che il nome comune corrisponda al nome host oppure al nome di dominio completo del server virtuale e che sia stato eseguito il provisioning dei certificati in tutti i nodi del cluster di failover.

- [!INCLUDE[ssKilimanjaro](../../includes/ssKilimanjaro-md.md)] e [!INCLUDE[ssKilimanjaro](../../includes/ssKilimanjaro-md.md)] Native Client (SNAC) supportano i certificati con caratteri jolly. SNAC è stato deprecato e sostituito con [Microsoft OLE DB Driver per SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) e [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md). È possibile che altri client non supportino i certificati con caratteri jolly. Per altre informazioni, vedere la documentazione del client e [KB 258858](https://support.microsoft.com/kb/258858).       
  Non è possibile selezionare il certificato con caratteri jolly usando Gestione configurazione SQL Server. Per usare un certificato con caratteri jolly, è necessario modificare la chiave del Registro di sistema `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQLServer\SuperSocketNetLib` e immettere l'identificazione personale del certificato, senza spazi, nel valore **Certificato**.  

  > [!WARNING]  
  > [!INCLUDE[ssnoteregistry_md](../../includes/ssnoteregistry-md.md)]  

## <a name="to-provision-install-a-certificate-on-a-single-server"></a>Per installare e rendere disponibile un certificato in un solo server  
Con [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)], la gestione dei certificati è integrata in Gestione configurazione SQL Server. Gestione configurazione SQL Server per [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] può essere usato con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vedere [Gestione dei certificati (Gestione configurazione SQL Server)](../../database-engine/configure-windows/manage-certificates.md) per aggiungere un certificato in una sola istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Se si usa [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] e Gestione configurazione SQL Server per [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] non è disponibile, seguire questa procedura:

1. Fare clic sul menu **Start** , scegliere **Esegui**, digitare **MMC** nella casella **Apri** e fare clic su **OK**.  
  
2. Nella console MMC scegliere **Aggiungi/Rimuovi snap-in** dal menu **File**.  
  
3. Nella finestra di dialogo **Aggiungi/Rimuovi snap-in** fare clic su **Aggiungi**.  
  
4. Nella finestra di dialogo **Aggiungi snap-in autonomo** fare clic su **Certificati**e quindi su **Aggiungi**.  
  
5. Nella finestra di dialogo **Snap-in certificati** fare clic su **Account del computer**e quindi su **Fine**.  
  
6. Nella finestra di dialogo **Aggiungi snap-in autonomo** fare clic su **Chiudi**.  
  
7. Nella finestra di dialogo **Aggiungi/Rimuovi snap-in** fare clic su **OK**.  
  
8. Nello snap-in **Certificati** espandere **Certificati**e **Personale**, fare clic con il pulsante destro del mouse su **Certificati**, scegliere **Tutte le attività**e quindi fare clic su **Importa**.  

9. Fare clic con il pulsante destro del mouse sul certificato importato, scegliere **Tutte le attività**e quindi fare clic su **Gestisci chiavi private**. Nella finestra di dialogo **Sicurezza** aggiungere l'autorizzazione di lettura per l'account utente usato dall'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
10. Completare l' **Importazione guidata certificati**per aggiungere un certificato al computer e chiudere la console MMC. Per ulteriori informazioni sull'aggiunta di un certificato a un computer, vedere la documentazione di Windows.  
  
## <a name="to-provision-install-a-certificate-across-multiple-servers"></a>Per installare e rendere disponibile un certificato in più server
Con [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)], la gestione dei certificati è integrata in Gestione configurazione SQL Server. Gestione configurazione SQL Server per [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] può essere usato con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vedere [Gestione dei certificati (Gestione configurazione SQL Server)](../../database-engine/configure-windows/manage-certificates.md) per aggiungere un certificato in una configurazione del cluster di failover o in una configurazione del gruppo di disponibilità.

Se si usa [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] e Gestione configurazione SQL Server per [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] non è disponibile, seguire la procedura descritta nella sezione [Per installare e rendere disponibile un certificato in un solo server](#to-provision-install-a-certificate-on-a-single-server) per ogni server.

## <a name="to-export-the-server-certificate"></a>Per esportare il certificato del server  
  
1. Nello snap-in **Certificati** individuare il certificato nella cartella **Certificati** / **Personale** , fare clic con il pulsante destro del mouse su **Certificato**, scegliere **Tutte le attività**e quindi fare clic su **Esporta**.  
  
2. Completare l' **Esportazione guidata certificati**e archiviare il file di certificato in una posizione appropriata.  
  
## <a name="to-configure-the-server-to-force-encrypted-connections"></a>Per configurare il server per imporre le connessioni crittografate

> [!IMPORTANT]
> L'account del servizio SQL Server deve avere le autorizzazioni di lettura per il certificato usato per forzare la crittografia in SQL Server. Per un account del servizio senza privilegi, sarà necessario aggiungere le autorizzazioni di lettura al certificato. In caso contrario, il riavvio del servizio SQL Server potrebbe non riuscire.
  
1. In **Gestione configurazione SQL Server** espandere **Configurazione di rete SQL Server**, fare clic con il pulsante destro del mouse su **Protocolli per** _\<istanza server>_ e quindi scegliere**Proprietà**.  
  
2. Nella scheda **Certificato** della finestra di dialogo **Proprietà** - **Protocolli per** _\<nome istanza>_ selezionare il certificato desiderato nell'elenco a discesa per la casella **Certificato** e quindi fare clic su **OK**.  
  
3. Nella casella **ForceEncryption** della scheda **Flag** selezionare **Sì**e quindi fare clic su **OK** per chiudere la finestra di dialogo.  
  
4. Riavviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

> [!NOTE]
> Per garantire connettività sicura tra client e server, configurare il client in modo che richieda connessioni crittografate. Altre dettagli sono spiegati [più avanti in questo articolo](#to-configure-the-client-to-request-encrypted-connections).

## <a name="to-configure-the-client-to-request-encrypted-connections"></a>Per configurare il client in modo che richieda connessioni crittografate  

1. Copiare il certificato originale o il file di certificato esportato nel computer client.  
  
2. Nel computer client usare lo snap-in **Certificati** per installare il certificato radice o il file di certificato esportato.  
  
3. Usando Gestione configurazione SQL Server, fare clic con il pulsante destro del mouse su **Configurazione SQL Server Native Client** e quindi fare clic su **Proprietà**.  
  
4. Nella casella **Imponi crittografia protocolli** della pagina **Flag** fare clic su **Sì**.  
  
## <a name="to-encrypt-a-connection-from-sql-server-management-studio"></a>Per crittografare una connessione da SQL Server Management Studio  
  
1. Nella barra degli strumenti di Esplora oggetti fare clic su **Connetti**e quindi su **Motore di database**.  
  
2. Nella finestra di dialogo **Connetti al server** completare le informazioni di connessione e quindi fare clic su **Opzioni**.  
  
3. Nella scheda **Proprietà connessione** fare clic su **Crittografa connessione**.  

## <a name="internet-protocol-security-ipsec"></a>Internet Protocol Security (IPSec)
Per crittografare i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante la trasmissione, è possibile usare IPSec, che è disponibile nei sistemi operativi client e server e non richiede alcuna configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per informazioni su IPSec, vedere la documentazione della rete o di Windows.

## <a name="see-also"></a>Vedere anche
[Supporto di TLS 1.2 per Microsoft SQL Server](https://support.microsoft.com/kb/3135244)     
[Configurare Windows Firewall per consentire l'accesso a SQL Server](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)     
