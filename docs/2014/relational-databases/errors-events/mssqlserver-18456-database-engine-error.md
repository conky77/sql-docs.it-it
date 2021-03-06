---
title: MSSQLSERVER_18456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
ms.assetid: c417631d-be1f-42e0-8844-9f92c77e11f7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f37f2ce9ec367d136eb853ce3bffe81f22b2dc4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62869596"
---
# <a name="mssqlserver_18456"></a>MSSQLSERVER_18456
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|18456|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LOGON_FAILED|  
|Testo del messaggio|Accesso non riuscito per l'utente '%.*ls'.%.\*ls|  
  
## <a name="explanation"></a>Spiegazione  
 Quando un tentativo di connessione viene rifiutato a causa di un errore di autenticazione dovuto a una password o un nome utente errato, al client viene restituito un messaggio simile al seguente:  "Accesso non riuscito per l'utente '<nome_utente>' (Microsoft SQL Server, Errore: 18456)".  
  
 Al client vengono restituite informazioni aggiuntive tra cui le seguenti:  
  
 "Accesso non riuscito per l'utente '<nome_utente>' (provider di dati SqlClient .Net)"  
  
 -----------------------------\-  
  
 "Nome server: <nome_computer>"  
  
 "Numero errore: 18456"  
  
 "Gravità: 14"  
  
 "Stato: 1"  
  
 "Numero riga: 65536"  
  
 Può essere inoltre restituito il messaggio seguente:  
  
 "Messaggio 18456, livello 14, stato 1, server <nome_computer>, riga 1"  
  
 "Accesso non riuscito per l'utente '<nome_utente>'".  
  
## <a name="additional-error-information"></a>Informazioni aggiuntive sull'errore  
 Per aumentare il livello di sicurezza, il messaggio di errore restituito al client nasconde deliberatamente la natura dell'errore di autenticazione. Tuttavia, nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ogni errore viene indicato lo stato corrispondente tramite cui viene eseguito il mapping alla condizione di errore di autenticazione. Confrontare lo stato di errore restituito con l'elenco seguente per determinare il motivo dell'errore di accesso.  
  
|State|Descrizione|  
|-----------|-----------------|  
|1|Non sono disponibili informazioni sull'errore. Questo stato in genere indica che non si dispone dell'autorizzazione a ricevere i dettagli dell'errore. Per ulteriori informazioni, contattare l'amministratore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|2|L'ID utente non è valido.|  
|5|L'ID utente non è valido.|  
|6|Si è tentato di utilizzare un account di accesso di Windows con l'autenticazione di SQL Server.|  
|7|L'account di accesso è disabilitato e la password non è corretta.|  
|8|La password non è corretta.|  
|9|La password non è valida.|  
|11|L'account di accesso è valido, ma l'accesso al server ha avuto esito negativo. Una possibile causa di questo errore è quando l'utente di Windows dispone dell'accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come un membro del gruppo Administrators locale, ma Windows non fornisce le credenziali di amministratore. Per connettersi, avviare il programma di connessione usando l'opzione **Esegui come amministratore** e quindi aggiungere l'utente di Windows a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come accesso specifico.|  
|12|L'account di accesso è valido, ma l'accesso al server ha avuto esito negativo.|  
|18|È necessario modificare la password.|  
  
 Esistono altri stati di errore che indicano un errore di elaborazione interno non previsto.  
  
 **Un'altra possibile cause insolita**  
  
 Il motivo dell'errore **un tentativo di accesso con l'autenticazione SQL non è riuscito. Il server è configurato solo per l'autenticazione di Windows.** può essere restituito nelle situazioni seguenti.  
  
-   Quando il server è configurato per l'autenticazione in modalità mista, in una connessione ODBC viene utilizzato il protocollo TCP e tramite la connessione non viene specificato in modo esplicito che in essa deve essere utilizzata una connessione trusted.  
  
-   Quando il server è configurato per l'autenticazione in modalità mista, in una connessione ODBC vengono utilizzate named pipe, le credenziali utilizzate dal client per aprire la named pipe vengono utilizzate per rappresentare automaticamente l'utente e tramite la connessione non viene specificato in modo esplicito che in essa deve essere utilizzata una connessione trusted.  
  
 Per risolvere questo problema, includere `TRUSTED_CONNECTION = TRUE` nella stringa di connessione.  
  
## <a name="examples"></a>Esempi  
 In questo esempio, lo stato dell'errore di autenticazione è 8 e indica che la password non è corretta.  
  
|Data|Source (Sorgente)|Message|  
|----------|------------|-------------|  
|2007-12-05 20:12:56.34|Accesso|Errore: 18456, gravità: 14, stato: 8.|  
|2007-12-05 20:12:56.34|Accesso|Accesso non riuscito per l'utente '<nome_utente>'. [CLIENT: \<indirizzo IP>]|  
  
> [!NOTE]  
>  Se durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si usa la modalità Autenticazione di Windows e successivamente si passa alla modalità Autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e di Windows, l'account di accesso **sa** verrà inizialmente disabilitato. Questo causa l'errore di stato 7: "accesso non riuscito per l'utente ' sa '". Per abilitare l'account di accesso **sa** , vedere [modifica della modalità di autenticazione del server](../../database-engine/configure-windows/change-server-authentication-mode.md).  
  
## <a name="user-action"></a>Azione dell'utente  
 Se si sta tentando di effettuare la connessione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], verificare che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia configurato in modalità Autenticazione mista.  
  
 Se si sta tentando di effettuare la connessione mediante l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , verificare che l'account di accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esista e che non contenga errori di ortografia.  
  
 Se si sta tentando di effettuare la connessione mediante l'autenticazione di Windows, verificare di essere connessi al dominio corretto.  
  
 Se l'errore indica lo stato 1, contattare l'amministratore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se si tenta di eseguire la connessione usando le credenziali di amministratore, avviare l'applicazione usando l'opzione **Esegui come amministratore**. Dopo aver stabilito la connessione, aggiungere l'utente di Windows come singolo account di accesso.  
  
 Se il [!INCLUDE[ssDE](../../includes/ssde-md.md)] supporta i database indipendenti, verificare che l'account di accesso non sia stato eliminato dopo la migrazione a un utente del database indipendente.  
  
 Quando ci si connette in locale a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le connessioni da servizi in esecuzione con **NT AUTHORITY\NETWORK SERVICE** devono essere autenticate usando computer con nomi di dominio completi. Per altre informazioni, vedere [Procedura: Usare l'account Servizio di rete per accedere alle risorse in ASP.NET](https://msdn.microsoft.com/library/ff647402.aspx)  
  
  
