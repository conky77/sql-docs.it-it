---
title: Correzione automatica della pagina (per i gruppi di disponibilità e il mirroring del database) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- automatic page repair
- Availability Groups [SQL Server], automatic page repair
- database mirroring [SQL Server], automatic page repair
- suspect pages [SQL Server]
ms.assetid: cf2e3650-5fac-4f34-b50e-d17765578a8e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f4f39024817d3d0aa35c015ed815eb8f412f1c8e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63137508"
---
# <a name="automatic-page-repair-for-availability-groups-and-database-mirroring"></a>Correzione di pagina automatica (per Gruppi di disponibilità e Mirroring del database)
  La correzione automatica della pagina è supportata dal mirroring del database e da [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]. Se una pagina viene danneggiata e resa illeggibile a causa di determinati tipi di errori, viene tentato il relativo recupero automatico tramite un partner di mirroring di database (principale o mirror) o una replica di disponibilità (primaria o secondaria). Dal partner o dalla replica che non è grado di leggere la pagina viene richiesta una copia aggiornata di quest'ultima dal relativo partner o da un'altra replica. Se la richiesta viene soddisfatta, la pagina illeggibile viene sostituita dalla copia leggibile. In questo modo, l'errore viene in genere risolto.  
  
 In generale, gli errori di I/O possono essere gestiti dal mirroring del database e da [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] in modi equivalenti. Di seguito sono illustrate in modo esplicito le poche differenze.  
  
> [!NOTE]  
>  La correzione automatica della pagina è diversa dalla correzione DBCC. La correzione automatica della pagina consente di mantenere tutti i dati. La correzione di errori con l'opzione DBCC_REPAIR_ALLOW_DATA_LOSS può invece richiedere l'eliminazione di alcune pagine, con una conseguente perdita di dati.  
  
  
  
##  <a name="ErrorTypes"></a>Tipi di errore che provocano un tentativo di correzione automatica della pagina  
 Durante la correzione automatica delle pagine tramite mirroring del database, viene eseguito il tentativo di ripristinare solo le pagine in un file di dati in cui non è stato possibile completare un'operazione, a causa di uno degli errori elencati nella tabella seguente.  
  
|Numero di errore|Descrizione|Istanze che provocano un tentativo di correzione automatica della pagina|  
|------------------|-----------------|---------------------------------------------------------|  
|[823](../../relational-databases/errors-events/mssqlserver-823-database-engine-error.md)|Viene eseguita un'azione solo se il sistema operativo ha eseguito un controllo di ridondanza ciclico (CRC, Cyclic Redundancy Check) che ha generato un errore sui dati.|ERROR_CRC. Il valore del sistema operativo per questo errore è 23.|  
|[824](../../relational-databases/errors-events/mssqlserver-824-database-engine-error.md)|Errori logici.|Errori logici dei dati, come ad esempio un errore di checksum relativo a una pagina danneggiata o di scrittura incompleta.|  
|829|Una pagina contrassegnata come "ripristino in sospeso".|Tutti.|  
  
 Per visualizzare gli errori CRC 823 e gli errori 824 recenti, vedere la tabella [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) nel database [msdb](../../relational-databases/databases/msdb-database.md).  
  
  
  
##  <a name="UnrepairablePageTypes"></a>Tipi di pagina che non possono essere corretti automaticamente  
 La correzione automatica della pagina non può ripristinare i tipi di pagine di controllo seguenti:  
  
-   Pagina di intestazione del file (ID pagina 0).  
  
-   Pagina 9 (pagina di avvio del database).  
  
-   Pagine di allocazione: pagine mappa di allocazione globale (GAM, Global Allocation Map), pagine mappa di allocazione globale condivisa (SGAM, Shared Global Allocation Map) e pagine spazio libero nella pagina (PFS, Page Free Space).  
  

  
##  <a name="PrimaryIOErrors"></a>Gestione degli errori di I/O nel database principale o primario  
 Nel database principale o primario, la correzione automatica della pagina è possibile solo quando il database è nello stato SINCRONIZZATO e tramite esso si stanno ancora inviando record di log per il database al database mirror o secondario. La sequenza di azioni di base in un tentativo di correzione automatica della pagina è la seguente:  
  
1.  Quando si verifica un errore di lettura in una pagina di dati nel database principale o primario, tramite quest'ultimo viene inserita una riga nella tabella [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) con lo stato di errore appropriato. Per il mirroring del database, dal database principale viene richiesta una copia della pagina dal database mirror. Per [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], tramite il database primario viene trasmessa la richiesta a tutti i database secondari e la pagina viene restituita dal primo a rispondere. Nella richiesta viene specificato l'ID della pagina e il numero LSN presente attualmente al termine del log scaricato. La pagina è contrassegnata come *ripristino in sospeso*. In questo modo non sarà possibile accedervi durante il tentativo di correzione automatica della pagina. L'accesso a questa pagina durante il tentativo di correzione non verrà consentito e sarà visualizzato l'errore 829 (ripristino in sospeso).  
  
2.  Dopo aver ricevuto la richiesta della pagina, dal database mirror o secondario viene atteso il completamento del rollforward del log fino al numero LSN specificato nella richiesta. Successivamente, tramite il database mirror o secondario si tenta di accedere alla pagina nella relativa copia del database. Se è possibile accedere alla pagina, la copia della pagina al database principale o primario viene inviata dal database mirror o secondario. In caso contrario, tramite il database mirror o secondario viene restituito un errore al database principale o primario e il tentativo di correzione automatica della pagina non verrà completato.  
  
3.  Il database principale o primario consente di elaborare la risposta contenente la copia aggiornata della pagina.  
  
4.  Una volta completata la correzione automatica di una pagina sospetta, la pagina viene contrassegnata nella tabella **suspect_pages** come ripristinata (**event_type** = 5).  
  
5.  Se l'errore di I/O della pagina ha causato una qualsiasi [transazione posticipata](../../relational-databases/backup-restore/deferred-transactions-sql-server.md), una volta corretta la pagina, tramite il database principale o primario viene tentato di risolvere queste transazioni.  
  

  
##  <a name="SecondaryIOErrors"></a>Gestione degli errori di I/O nel database mirror o secondario  
 Gli errori di I/O nelle pagine di dati che si verificano nel database mirror o secondario sono gestiti in genere nello stesso modo dal mirroring del database e da [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
1.  Con il mirroring del database, se vengono rilevati errori di I/O in una o più pagine dal database mirror quando tramite quest'ultimo viene eseguito il rollforward di un record di log, per la sessione di mirroring viene attivato lo stato SOSPESO. Con [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], se vengono rilevati errori di I/O in una o più pagine da una replica secondaria quando tramite quest'ultima viene eseguito il rollforward di un record di log, per il database secondario viene attivato lo stato SOSPESO. A questo punto, il database mirror o secondario inserisce una riga con la stato di errore appropriato nella tabella **suspect_pages** . Dal database mirror o secondario viene quindi richiesta una copia della pagina dal database principale o primario.  
  
2.  Tramite il database principale o primario si tenta di accedere alla pagina nella relativa copia del database. Se è possibile accedere alla pagina, la copia della pagina al database mirror o secondario viene inviata dal database principale o primario.  
  
3.  Se dal database mirror o secondario si riceve una copia di tutte le pagine richieste, tramite questo database si tenta di riprendere la sessione di mirroring. Se la correzione automatica di una pagina sospetta viene eseguita, la pagina viene contrassegnata nella tabella **suspect_pages** come ripristinata (**event_type** = 4).  
  
     Se da un database mirror o secondario non si riceve una pagina richiesta dal database principale o primario, il tentativo di correzione automatica della pagina non verrà completato. Con il mirroring del database, la sessione di mirroring rimane sospesa. Con [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], il database secondario rimane sospeso. Se la ripresa della sessione di mirroring o del database secondario viene eseguita manualmente, le pagine danneggiate verranno rilevate nuovamente durante la fase di sincronizzazione.  

  
##  <a name="DevBP"></a>Procedura consigliata per gli sviluppatori  
 La correzione automatica di una pagina è un processo asincrono eseguito in background. Pertanto, non sarà possibile completare un'operazione sul database tramite cui viene richiesta una pagina illeggibile e verrà restituito il codice di errore relativo alla condizione che lo ha causato. In fase di sviluppo di un'applicazione per un database con mirroring o un database di disponibilità, è consigliabile intercettare le eccezioni per le operazioni con errori. Se il codice di errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è 823, 824 o 829, ripetere l'operazione in un secondo momento.  
  

  
##  <a name="ViewAPRattempts"></a>Procedura: visualizzare i tentativi di correzione automatica della pagina  
 Tramite le DMV seguenti vengono restituite righe degli ultimi tentativi di correzione automatica delle pagine in un database di disponibilità o database con mirroring specificato, con un massimo di 100 righe per database.  
  
-   **Gruppi di disponibilità AlwaysOn:**  
  
     [sys. dm_hadr_auto_page_repair &#40;&#41;Transact-SQL](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-auto-page-repair-transact-sql)  
  
     Restituisce una riga per ogni tentativo di correzione automatica della pagina in qualsiasi database di disponibilità in una replica di disponibilità ospitata per qualsiasi gruppo di disponibilità dall'istanza del server.  
  
-   **Mirroring del database:**  
  
     [sys. dm_db_mirroring_auto_page_repair &#40;&#41;Transact-SQL](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-auto-page-repair)  
  
     Viene restituita una riga per ogni tentativo di correzione automatica della pagina in qualsiasi database con mirroring nell'istanza del server.  
  
 
  
## <a name="see-also"></a>Vedere anche  
 [Gestire la tabella suspect_pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)   
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
