---
title: Note sulla versione di Reporting Services 2017 e versioni successive | Microsoft Docs
ms.date: 12/04/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.reviewer: maggies
author: casualoak
ms.author: rhys
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 39049ee5a2561821e0a2284ed66b9b04730998bf
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "74834255"
---
# <a name="release-notes-for-sql-server-reporting-services-ssrs-2017-and-later"></a>Note sulla versione per SQL Server Reporting Services (SSRS) 2017 e versioni successive

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017-and-later](../includes/ssrs-appliesto-2017-and-later.md)]

Questo articolo descrive le modifiche a [!INCLUDE[ssnoversion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) 2017 e versioni successive.

Per le note sulla versione relative ai controlli di Visualizzatore report, vedere [Note sulla versione per i controlli Visualizzatore report per WebForms e WinForms di SSRS](application-integration/release-notes-ssrs-application-integration.md).

<!--
We are "standardizing" all our 'Release Notes' style articles:

  - File names:   'release-notes-[TechArea-Name].md'


  - Content format:   2-column tables.  No longer using bullet lists.

    - Ideally, the 'Details' column should contain a link to another SSRS documentation article wherein the particular issue fix is discussed in any way.  Or if there is more to say beyond one sentence, the other sentences of elaboration would go into the 'Details' column.


  - H2 header names are kept short, for better display.


  - Try to keep all Release Notes in one .md file.  Avoid having multiple R.N. files whose names differ only by version or date.

    - Seriously consider erasing info about ancient releases that are so old that nobody cares about them anymore.  If you really want to retain ancient info, consider doing so in an HTML comment at the end of the .md file, just in case a Microsoft employee needs to re-examine ancient info.  In any case, this file cannot get ever longer, and some deletion or hiding of oldest info must eventually occur.


  - Do use '::: moniker range=' zones when version 2017 is no longer the only version represented inside this .md file.

    - Use the '=' operator on the moniker, not the '>=' operator.
    - In contrast, in our 'Whats New' articles we do use the '>=', rather than '='.

GeneMi, DevOps = 1467988 (MsEng > TechnicalContent) , 2019/03/19
-->
## <a name="1406001451-20191113"></a>14.0.600.1451 2019/11/13 

| Problema risolto | Dettagli |
| :---------- | :------ |
| Aggiornamenti per la sicurezza | &nbsp; |
| I report impaginati non funzionavano correttamente con i parametri di filtro quando era abilitato lo snapshot  | &nbsp; |
| Gli utenti con ruolo Visualizzazione e impostazioni predefinite non avevano le autorizzazioni per scaricare file di Excel  | &nbsp; |
| Non era possibile eseguire l'aggiornamento al server di report di Power BI da SQL Server 2016 Reporting Services | &nbsp; |
| Dopo l'aggiornamento da SQL Server 2012 Reporting Services, le sottoscrizioni non riuscivano e veniva visualizzato il messaggio "L'intestazione del messaggio contiene un carattere non valido:" | &nbsp; |
| Strumento di configurazione: l'annullamento delle finestre modali nella sezione Database causava il riavvio del servizio Reporting Services | &nbsp; |
| Il rendering dell'espressione di proprietà BorderStyle dei controlli TextBox non veniva eseguito in formato Excel  | &nbsp; |
| Un problema di impaginazione faceva sì che per alcuni report venisse ripetuto il rendering della stessa pagina, senza che venisse mai raggiunta l'ultima pagina del report | &nbsp; |

## <a name="1406001274-20190701"></a>14.0.600.1274, 01/07/2019

| Problema risolto | Dettagli |
| :---------- | :------ |
| Aggiornamenti per la sicurezza | &nbsp; |
| Non è possibile selezionare i giorni della settimana durante la creazione di una pianificazione settimanale condivisa | &nbsp; |
| Il report non visualizza correttamente i ritorni a capo in formato Word | &nbsp; |
| System Center Operations Manager (SCOM) 2019 non funziona più con gli aggiornamenti di SSRS 2017 recenti | &nbsp; |
| Errore durante la chiamata dell'estensione di autorizzazione per set di dati condivisi | &nbsp; |
| A causa di una modifica della logica nella stored procedure GetAllProperties in SSRS 2017 e nel server di report di Power BI, il metodo ReportingService2010.GetProperties dell'endpoint servizio Web non riesce a recuperare dati per il report collegato | &nbsp; |
| L'intestazione delle righe nelle griglie semplici dei report per dispositivi mobili scompare quando si fa clic su un elemento all'interno della griglia | &nbsp; |
| Non è possibile usare un campo data in un parametro di una sottoscrizione guidata dai dati | &nbsp; |
| La Tablix annidata visualizza caratteri piccoli o parziali in SSRS 2016 e versioni successive | &nbsp; |
| Le sottoscrizioni con un parametro DateTime visualizzano un errore dopo essere state modificate da un utente con impostazioni locali diverse | &nbsp; |
| La creazione di una sottoscrizione guidata dai dati con estensione per il recapito Null non riesce e viene visualizzato un "Errore di recapito" | &nbsp; |
| La codifica dell'URL non è corretta se si imposta il valore in formato Excel\Word | &nbsp; |

## <a name="1406001109-20190212"></a>14.0.600.1109, 12/02/2019

| Problema risolto | Dettagli |
| :---------- | :------ |
| Le pianificazioni degli snapshot dei report di cache diventano "Pianificazione in base al report" dopo la modifica della sottoscrizione. | &nbsp; |
| rc:Toolbar=false non funziona nell'edizione Express. | &nbsp; |
| Non viene eseguito correttamente il rendering di alcuni caratteri thai durante l'esportazione di report impaginati in formato PDF. | &nbsp; |
| Si verifica un deadlock durante la notifica del completamento di sottoscrizioni guidate dai dati. | &nbsp; |
| In alcune circostanze, le immagini incorporate non vengono visualizzate quando viene usato il parametro rc:Toolbar=False. | &nbsp; |
| Non è possibile creare sottoscrizioni guidate dai dati per report che usano parametri a cascata. | &nbsp; |
| Non è possibile modificare le sottoscrizioni configurate con un intervallo non valido. | &nbsp; |
| Aggiornamenti per la sicurezza. | &nbsp; |
| Non viene visualizzata l'interfaccia utente dei report collegati. | &nbsp; |
| Alcuni report impaginati con controlli di un'area dati Tablix annidata hanno tipi di carattere non corretti. | &nbsp; |
| In alcuni report impaginati contenenti aree dati Tablix vengono erroneamente aggiunti spazi vuoti. | &nbsp; |
| Le righe di intestazione spariscono quando si espandono le griglie dati semplici di report per dispositivi mobili. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600906-20180912"></a>14.0.600.906, 12/09/2018

È stato corretto il problema seguente:

| Problema risolto | Dettagli |
| :---------- | :------ |
| L'autenticazione personalizzata non restituisce informazioni sui cookie corrette. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600892-20180831"></a>14.0.600.892, 31/08/2018

| Problema risolto | Dettagli |
| :---------- | :------ |
| La presenza di una casella di testo all'interno di un rettangolo impedisce l'ingrandimento in verticale del rettangolo quando rc:Toolbar=False e contiene testo lungo. | &nbsp; |
| Le dimensioni del testo non vengono adattate se pageHeight è minore di 0,5 pollici. | &nbsp; |
| Si verifica un deadlock nel database del catalogo di SSRS quando il database viene usato con CRM. | &nbsp; |
| Le intestazioni di colonna con allineamento verticale non vengono visualizzate correttamente quando si scorre verso il basso nel report. | &nbsp; |
| Per gli utenti aggiunti al ruolo report di System Center Operations Manager viene bloccato l'accesso al portale Web SSRS. | &nbsp; |
| I caratteri thai non vengono esportati correttamente in PDF. | &nbsp; |
| Modifica del comportamento del ruolo browser. | &nbsp; |
| rc:Toolbar=false non funziona nell'edizione Express. | &nbsp; |
| Barra di scorrimento verticale mancante nell'area dei messaggi di richiesta per i parametri. | &nbsp; |
| Aggiornamento del runtime per i report per dispositivi mobili. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600744-20180425"></a>14.0.600.744, 25/04/2018

| Problema risolto | Dettagli |
| :---------- | :------ |
| La pagina Sottoscrizione guidata dai dati non visualizza l'opzione di recapito dopo la creazione. | &nbsp; |
| Se si esegue l'aggiornamento da SSRS 2012 a SSRS 2017, RSManagement genererà un'eccezione a intervalli di pochi secondi. | &nbsp; |
| Non è possibile modificare i valori predefiniti per i parametri multivalore in IE11. | &nbsp; |
| Le pianificazioni sono vuote quando viene eseguita una pianificazione condivisa. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600689-20180228"></a>14.0.600.689, 28/02/2018

| Problema risolto | Dettagli |
| :---------- | :------ |
| La visibilità di Parametro report in un report collegato viene ripristinata dopo la modifica delle relative proprietà. | &nbsp; |
| Il parametro URL rc:Toolbar=false non funziona nell'edizione Express. | &nbsp; |
| Se una casella di testo contiene espressioni e la sua proprietà CanGrow è impostata su false, i suoi valori non vengono visualizzati. | &nbsp; |
| Aggiunta del collegamento _Ulteriori informazioni_ per il codice Product Key nel programma di installazione. | &nbsp; |
| Il portale Web con autenticazione basata su form personalizzata ignora il cookie di scadenza variabile. | &nbsp; |
| L'esportazione in Word crea altezze di righe non uniformi se il contenuto della riga è vuoto. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="140600594-20180109"></a>14.0.600.594, 09/01/2018

Sono stati implementati alcuni aggiornamenti della sicurezza.

### <a name="140600490-20171101"></a>14.0.600.490, 01/11/2017

Problemi risolti con l'aggiornamento dello SKU.

## <a name="140600451-20170930"></a>14.0.600.451, 30/09/2017

Versione iniziale.

## <a name="next-steps"></a>Passaggi successivi

[Novità di Reporting Services (SSRS)](what-s-new-in-sql-server-reporting-services-ssrs.md)

Altre domande? [Visitare il forum su Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
