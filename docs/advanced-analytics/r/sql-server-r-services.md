---
title: Che cos'è R Services per SQL Server 2016?
titleSuffix: ''
description: R Services è una funzionalità di SQL Server 2016 che offre la possibilità di eseguire script R con dati relazionali. È possibile usare pacchetti e framework open source, oltre ai pacchetti di Microsoft R per l'analisi predittiva e le funzioni di Machine Learning. Gli script vengono eseguiti nel database senza trasferire i dati all'esterno di SQL Server o in rete. Questo articolo illustra le nozioni di base di R Services per SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/12/2019
ms.topic: overview
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 48f3b3433d0ca2f4daf08048228989598c5cf36a
ms.sourcegitcommit: 1b0906979db5a276b222f86ea6fdbe638e6c9719
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971429"
---
# <a name="what-is-sql-server-2016-r-services"></a>Che cos'è R Services per SQL Server 2016?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

R Services è una funzionalità di SQL Server 2016 che offre la possibilità di eseguire script R con dati relazionali. È possibile usare pacchetti e framework open source, oltre ai [pacchetti di Microsoft R](#packages) per l'analisi predittiva e le funzioni di Machine Learning. Gli script vengono eseguiti nel database senza trasferire i dati all'esterno di SQL Server o in rete. Questo articolo illustra le nozioni di base di R Services per SQL Server.

> [!Note]
> La funzionalità R Services, rinominata in [Machine Learning Services](../what-is-sql-server-machine-learning.md) in SQL Server 2017 e versioni successive, supporta sia Python che R.

## <a name="what-is-r-services"></a>Che cos'è R Services?

R Services per SQL Server consente di eseguire script R all'interno del database. È possibile usare questa funzionalità per preparare e pulire i dati, eseguire la progettazione delle caratteristiche e il training, la valutazione e la distribuzione di modelli di Machine Learning all'interno di un database. La funzionalità esegue gli script nella posizione in cui i dati risiedono, eliminando la necessità di trasferire i dati in rete in un altro server.

Le distribuzioni di base di R sono incluse in R Services. È possibile usare pacchetti e framework open source in aggiunta ai pacchetti Microsoft [RevoScaleR](../r/ref-r-revoscaler.md), [MicrosoftML](../r/ref-r-microsoftml.md), [olapR]../r/ref-r-olapr.md) e [sqlrutils](../r/ref-r-sqlrutils.md) per R.

Per eseguire gli script R in SQL Server, R Services usa un framework di estendibilità. Altre informazioni sono disponibili in:

+ [Framework di estendibilità](../concepts/extensibility-framework.md)
+ [Estensione di R](../concepts/extension-r.md)

## <a name="what-can-i-do-with-r-services"></a>Che cosa è possibile fare con R Services?

È possibile usare R Services per compilare ed eseguire il training di modelli di Machine Learning e Deep Learning all'interno di SQL Server. In R Services è anche possibile distribuire modelli esistenti e usare dati relazionali per le stime.

Tra gli esempi del tipo di stime per cui è possibile usare R Services per SQL Server rientrano:

|||
|-|-|
|Classificazione/categorizzazione|Suddivisione automatica dei commenti e dei suggerimenti degli utenti in categorie positive e negative|
|Regressione/stima di valori continui|Previsione del prezzo delle case in base alle dimensioni e alla posizione|
|Anomaly Detection|Rilevamento di transazioni bancarie fraudolente |
|Consigli|Suggerimento di prodotti che gli acquirenti online potrebbero voler acquistare, in base agli acquisti precedenti|

### <a name="how-to-execute-r-scripts"></a>Come eseguire script R

In R Services è possibile eseguire script R in due modi:

+ Il modo più comune consiste nell'usare la stored procedure T-SQL [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

+ È anche possibile usare il client R preferito e scrivere script che eseguono il push dell'esecuzione (detta *contesto di calcolo remoto*) a un'istanza di SQL Server remota. Per altre informazioni, vedere come [configurare lo sviluppo in R di un client di data science](../r/set-up-a-data-science-client.md).

<a name="version"></a>

## <a name="r-version"></a>Versione di R

R versione 3.2.2 è incluso in SQL Server 2016 R Services. Per le versioni più recenti di R, usare [Machine Learning Services per SQL Server 2017 e versioni successive](../what-is-sql-server-machine-learning.md).

<a name="packages"></a>

## <a name="r-packages"></a>Pacchetti R

È possibile usare pacchetti e framework open source, oltre ai pacchetti aziendali Microsoft. I pacchetti R open source più comuni sono pre-installati in R Services. Sono inclusi anche i pacchetti di Microsoft R seguenti:

| Pacchetto | Descrizione |
|-|-|
| [RevoScaleR](../r/ref-r-revoscaler.md) | Pacchetto principale per R scalabile. Trasformazioni e manipolazione di dati, riepilogo statistico, visualizzazione e molte forme di modellazione. Inoltre, le funzioni di questo pacchetto distribuiscono automaticamente i carichi di lavoro tra i core disponibili per l'elaborazione parallela. |
| [MicrosoftML (R)](../r/ref-r-microsoftml.md) | Aggiunge algoritmi di Machine Learning per creare modelli personalizzati per l'analisi del testo, l'analisi delle immagini e l'analisi del sentiment. |
| [olapR](../r/ref-r-olapr.md) | Funzioni R usate per le query MDX su un cubo OLAP di SQL Server Analysis Services. |
| [sqlrutils](../r/ref-r-sqlrutils.md) | Meccanismo per usare gli script R in una stored procedure T-SQL, registrare la stored procedure con un database ed eseguirla da un [ambiente di sviluppo R](../r/set-up-a-data-science-client.md). |
| [Microsoft R Open](https://mran.microsoft.com/rro) | Microsoft R Open (MRO) è la distribuzione avanzata di R di Microsoft. Si tratta di una piattaforma open source completa per analisi statistica e data science. Basata su R e compatibile al 100% con questo linguaggio, include funzionalità aggiuntive per migliorare le prestazioni e la riproducibilità. |

## <a name="how-do-i-get-started-with-rservices"></a>Come iniziare a usare R Services

1. [Installare R Services per SQL Server 2016](../install/sql-r-services-windows-install.md)

1. Configurare gli strumenti di sviluppo. È possibile usare:

    + [Azure Data Studio](../../azure-data-studio/what-is.md) o [SQL Server Management Studio (SSMS)](../../ssms/sql-server-management-studio-ssms.md) per usare T-SQL e la stored procedure [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) per l'esecuzione dello script R.
    + R nella workstation o nel portatile di sviluppo per l'esecuzione degli script. È possibile eseguire il pull dei dati in locale o il push dell'esecuzione in modalità remota a SQL Server con [RevoScaleR](../r/ref-r-revoscaler.md). Per altre informazioni, vedere come [configurare lo sviluppo in R di un client di data science](../r/set-up-a-data-science-client.md).

1. Scrivere il primo script R

    + Avvio rapido: [Creare ed eseguire script R semplici in SQL Server](../tutorials/quickstart-r-create-script.md)
    + Avvio rapido: [Creare ed eseguire il training di un modello predittivo in R](../tutorials/quickstart-r-train-score-model.md)
    + Esercitazione: [Usare R in T-SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md): esplorare dati, progettare caratteristiche, eseguire il training e la distribuzione di modelli ed eseguire stime (serie in cinque parti)
    + Esercitazione: [Usare R Services in R Tools](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md): esplorare dati, creare grafici e tracciati, progettare caratteristiche, eseguire il training e la distribuzione di modelli ed eseguire stime (serie in sei parti)

## <a name="next-steps"></a>Passaggi successivi

+ [Installare R Services per SQL Server 2016](../install/sql-r-services-windows-install.md)
+ [Configurare un client di data science per lo sviluppo in R](../r/set-up-a-data-science-client.md)