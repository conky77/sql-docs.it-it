---
title: Sottoscrizioni guidate dai dati | Microsoft Docs
ms.date: 05/20/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: ba009f62-0d4f-45e7-a27c-36fd5f0cd3a8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2791293f805f1e2c0d9bd39822bc3f452777c007
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "66175604"
---
# <a name="data-driven-subscriptions"></a>sottoscrizioni guidate dai dati
  Una sottoscrizione guidata dai dati consente di utilizzare i dati di sottoscrizione dinamici recuperati da un'origine dei dati esterna in fase di esecuzione. In una sottoscrizione guidata dai dati è inoltre possibile utilizzare testo statico e valori predefiniti specificati al momento della definizione della sottoscrizione. È possibile utilizzare le sottoscrizioni guidate dai dati per eseguire le operazioni seguenti:  
  
-    Distribuire un report a un elenco dinamico di Sottoscrittori. È possibile, ad esempio, utilizzare sottoscrizioni guidate dai dati per distribuire un report in una grande organizzazione nella quale i sottoscrittori cambiano da un mese all'altro oppure utilizzare altri criteri per determinare l'appartenenza a un gruppo da un gruppo di utenti esistente.  
  
-   Filtrare l'output del report utilizzando valori dei parametri di report recuperati in fase di esecuzione.  
  
-   Variare i formati di output del report e le opzioni di recapito per ogni recapito di report.  
  
 Una sottoscrizione guidata dai dati è costituita da più parti. Gli aspetti fissi di una sottoscrizione guidata dai dati sono definiti al momento della creazione della sottoscrizione e includono gli elementi seguenti:  
  
- Il report per cui è stata definita la sottoscrizione. Una sottoscrizione è sempre associata a un singolo report.  
  
- L'estensione per il recapito utilizzata per distribuire il report. È possibile specificare il recapito tramite posta elettronica del server di report, il recapito alla condivisione file, il provider recapito Null utilizzato per il precaricamento della cache oppure un'estensione per il recapito personalizzata. Non è possibile specificare più estensioni per il recapito in una singola sottoscrizione.  
  
- L'origine dei dati del Sottoscrittore. Quando si definisce una sottoscrizione, è necessario specificare una stringa di connessione all'origine dei dati che contenga i dati del Sottoscrittore. L'origine dei dati del Sottoscrittore non può essere specificata dinamicamente in fase di esecuzione.  
  
- La query utilizzata per selezionare i dati del Sottoscrittore deve essere specificata al momento della definizione della sottoscrizione. Non è possibile modificare la query in fase di esecuzione.  
  
 I valori dinamici utilizzati in una sottoscrizione guidata dai dati vengono ottenuti quando la sottoscrizione viene elaborata. Esempi di dati variabili che è possibile utilizzare in una sottoscrizione includono il nome del Sottoscrittore, l'indirizzo di posta elettronica, il formato di output desiderato o qualsiasi valore valido per un parametro di report. Per utilizzare valori dinamici in una sottoscrizione guidata dai dati, è necessario definire un mapping tra campi restituiti nella query e opzioni di recapito e parametri di report specifici. I dati variabili vengono recuperati da un'origine dei dati del Sottoscrittore ogni volta che la sottoscrizione viene elaborata.  
  
## <a name="requirements-for-using-data-driven-subscriptions"></a>Requisiti per l'utilizzo delle sottoscrizioni guidate dai dati

 La funzionalità relativa alle sottoscrizioni guidate dai dati non è disponibile in tutte le edizioni. Vi sono inoltre limiti al tipo di origini dati che è possibile utilizzare per recuperare i dati di sottoscrizione in fase di esecuzione. Nell'elenco seguente vengono fornite ulteriori informazioni sui requisiti:  

- Per altre informazioni sulle edizioni di SQL Server che supportano la funzionalità di sottoscrizione guidata dai dati, vedere [Funzionalità di SQL Server Reporting Services supportate nelle diverse edizioni](../reporting-services-features-supported-by-the-editions-of-sql-server-2016.md).  

- Per i dati di sottoscrizione, scegliere un'origine dei dati che offra informazioni sullo schema al server di report. I tipi di origini dati supportate possono essere dati relazionali di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Oracle, database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], dati del pacchetto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], origini dati ODBC e OLE DB. Per altre informazioni sui requisiti dell'origine dati del sottoscrittore, vedere [Utilizzare un'origine dei dati esterna per i dati del Sottoscrittore &#40;sottoscrizione guidata dai dati&#41;](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
## <a name="working-with-data-driven-subscriptions"></a>Utilizzo di sottoscrizioni guidate dai dati  
 Negli argomenti seguenti vengono fornite ulteriori informazioni sulle sottoscrizioni guidate dai dati.  
  
|Argomenti|Descrizione|  
|------------|-----------------|  
|[Creare, modificare ed eliminare le sottoscrizioni guidate dai dati](../../reporting-services/subscriptions/create-modify-and-delete-data-driven-subscriptions.md)|Illustra come creare, modificare o eliminare una sottoscrizione guidata dai dati.|  
|[Utilizzare un'origine dei dati esterna per i dati del Sottoscrittore &#40;sottoscrizione guidata dai dati&#41;](../../reporting-services/subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)|Include informazioni sulle origini dei dati che è possibile utilizzare per una sottoscrizione guidata dai dati.|  
|[Creare una sottoscrizione guidata dai dati &#40;esercitazione su SSRS&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)|Include istruzioni dettagliate per la creazione di una sottoscrizione guidata dai dati.|  
|[Memorizzazione dei report nella cache &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)|Descrive come utilizzare Provider recapito Null con una sottoscrizione guidata dai dati per precaricare la cache.|  
  
## <a name="see-also"></a>Vedere anche

 [Sottoscrizioni e recapito &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)  
 [Precaricare la cache &#40;portale Web&#41;](../../reporting-services/report-server/preload-the-cache-report-manager.md)  
  
  
