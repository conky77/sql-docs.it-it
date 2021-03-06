---
title: Elenco di bug risolti | Microsoft Docs
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-chojas
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: a3143595a5e76331dfc61a8edca7b4f068cdc57c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76911255"
---
# <a name="list-of-bugs-fixed"></a>Elenco di bug risolti

Questa pagina contiene un elenco dei bug risolti in ogni versione, a partire da [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

### <a name="bug-fixes-in-the-msconame-odbc-driver-175-for-ssnoversion"></a>Correzioni di bug in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.5 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Correzione del calcolo hash dei metadati CMK di Azure Key Vault in Linux/Mac
- Correzione di un errore durante il caricamento di OpenSSL 1.0.0
- Correzione dei problemi di conversione durante l'uso delle tabelle codici ISO-8859-1 e ISO-8859-2
- Correzione del nome della libreria interna su Mac per includere il numero di versione
- Correzione dell'impostazione dell'indicatore Null per l'uso di associazioni con lunghezza e indicatore separati

### <a name="bug-fixes-in-the-msconame-odbc-driver-1742-for-ssnoversion"></a>Correzioni di bug in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.4.2 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

 - Correzione di un problema per cui l'ID del processo e il nome dell'applicazione non vengono inviati correttamente a SQL Server (per l'analisi di sys.dm_exec_sessions) (Linux)
 - Rimossa la dipendenza ridondante in libuuid (Linux)
 - Correzione di un bug con invio di dati UTF8 a SQL Server 2019
 - Correzione di un bug in cui le impostazioni locali che terminano con "@euro" non vengono rilevate correttamente (Linux)
 - Correzione per i dati XML restituiti in modo non corretto se recuperati come parametro di output durante l'uso di Always Encrypted

### <a name="bug-fixes-in-the-msconame-odbc-driver-174-for-ssnoversion"></a>Correzioni di bug in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.4 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Correzione dell'interruzione intermittente quando è abilitato MARS (Multiple Active Result Set)
- Correzione dell'interruzione della resilienza della connessione quando è abilitata la notifica asincrona
- Correzione dell'arresto anomalo del sistema durante il recupero dei record di diagnostica per i tentativi di connessione multithread
- Correzione di "Crittografia non supportata" al momento della riconnessione dopo la chiamata di SQLGetInfo() con SQL_USER_NAME e SQL_DATA_SOURCE_READ_ONLY
- Correzione dell'errore di inizializzazione COM durante l'autenticazione interattiva di Azure Active Directory
- Correzione di SQLGetData() per i dati UTF8 a più byte
- Correzione del recupero della lunghezza delle colonne sql_variant usando SQLGetData()
- Correzione dell'importazione delle colonne sql_variant che contengono più di 7992 byte con bcp
- Correzione dell'invio della codifica corretta al server per i dati di tipo carattere "narrow"

### <a name="bug-fixes-in-the-msconame-odbc-driver-173-for-ssnoversion"></a>Correzioni di bug in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.3 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Corretta la perdita di memoria del gestore eventi di invio notifica TCP
- Correzione del problema di ridefinizione dell'enumerazione _SQL_FILESTREAM_DESIRED_ACCESS nel file di intestazione msodbcsql.h
- Corretta la definizione mancante per ACCESS_TOKEN e AUTHENTICATION nel file di intestazione msodbcsql.h per Linux

### <a name="bug-fixes-in-the-msconame-odbc-driver-172-for-ssnoversion"></a>Correzioni di bug in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.2 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Corretto un messaggio di errore relativo all'autenticazione di Azure Active Directory
- Corretto il rilevamento della codifica quando le variabili di ambiente delle impostazioni locali sono impostate in modo diverso
- Corretto un arresto anomalo del sistema alla disconnessione con ripristino della connessione in corso
- Corretto il rilevamento dell'attività di connessione
- Corretto il rilevamento errato di socket chiusi
- Corretta l'attesa infinita durante il tentativo di rilasciare un handle di istruzione durante un ripristino non riuscito
- Corretto il comportamento di disinstallazione non corretto quando entrambe le versioni 13 e 17 sono installate in Windows
- Corretto il comportamento di decrittografia sulla piattaforma Windows precedente (Windows 7, 8 e Server 2012)
- Risolto un problema della cache quando si usa l'autenticazione ADAL in Windows
- Risolto un problema che causava il blocco e la sovrascrittura dei log di traccia in Windows

### <a name="bug-fixes-in-the-msconame-odbc-driver-171-for-ssnoversion"></a>Correzioni di bug in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17.1 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Corretto il ritardo di 1 secondo durante la chiamata di SQLFreeHandle con MARS abilitato e l'attributo di connessione "Encrypt = Yes"
- Corretto un errore 22003 di arresto anomalo del sistema in SQLGetData che si verifica quando la dimensione del buffer passato è inferiore ai dati recuperati (Windows)
- Corretti i messaggi di errore ADAL troncati
- Corretto un bug raro in Windows a 32 bit durante la conversione di un numero a virgola mobile in un valore intero
- Risolto un problema per cui l'inserimento di un valore double nel campo dei decimali con Always Encrypted attivo restituisce un errore di troncamento dei dati
- Corretto un avviso nel programma di installazione di MacOS
- Risolto lo stato di invio non corretto a SQL Server durante il tentativo di ripristino della sessione quando la resilienza della connessione e il pool di connessioni sono entrambi abilitati e la sessione non viene elaborata dal server

### <a name="bug-fixes-in-the-msconame-odbc-driver-17-for-ssnoversion"></a>Correzioni di bug in [!INCLUDE[msCoName](../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]

- Corretto un bug per cui quando si usa l'autenticazione Kerberos, l'inserimento bulk può non riuscire con l'errore "accesso negato"
- Rimossa la soluzione alternativa per un bug di unixODBC presente nella versione precedente alla 2.3.1 (il driver raddoppia le dimensioni di alcuni buffer passati a unixODBC)
- Corretta l'interruzione della resilienza della connessione (riconnessione) sospesa quando si usa ColumnEncryption=Enabled
- Corretto il bug di creazione DSN per cui, quando si usa l'opzione "Autenticazione interattiva di Active Directory", la finestra di autenticazione di Azure potrebbe non rispondere (Windows)
- Corretto un arresto anomalo raro del sistema durante l'arresto di ODBC quando è abilitata l'esecuzione asincrona (si verificava con la cancellazione dell'handle di connessione)
- Risolto un problema per cui il driver SQL causa un elevato consumo di CPU durante l'esecuzione di stored procedure lunghe
- Risolta l'impossibilità di recuperare dati in una colonna varbinary(max) crittografata senza conversione
- Risolto un problema a causa del quale, dopo il recupero di una colonna varchar(max) crittografata con valori Null usando SQLGetData() su un cursore statico, anche la colonna seguente viene annullata anche se contiene dati
- Risolto un problema relativo al recupero del campo varbinary(max) con Always Encrypted attivo
- Risolto un problema per cui setlocale() non funziona con Always Encrypted
- Risolto un problema per cui SQLDescribeParam() restituisce un errore se chiamato sul parametro di stored procedure di tipo XML con Always Encrypted attivo
- Corretti i caratteri di sottolineatura con escape non funzionanti in SQLTables
- Corretto un bug per cui i dati in ebraico (varchar) vengono troncati se restituiti come caratteri "wide" in Linux
- Risolto un problema di esecuzione di query sui tipi char/varchar con codifica Shift-JIS da un'applicazione UTF-8
- Corretto il bug per cui la chiamata di SQLGetInfo con il parametro SQL_DRIVER_NAME restituisce un nome file di Linux in MacOS
- Risolto un problema per cui caricare i dati character di Windows-1252 usando file di input di dimensioni superiori a 32 KB nelle colonne VARCHAR con l'utilità BCP genera errori
