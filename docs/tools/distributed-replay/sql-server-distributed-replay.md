---
title: SQL Server Distributed Replay
titleSuffix: SQL Server Distributed Replay
ms.prod: sql
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 58ef7016-b105-42c2-90a0-364f411849a4
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: c52325045cd21d0eb11edef8b0664d14c292e729
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "74993421"
---
# <a name="sql-server-distributed-replay"></a>SQL Server Distributed Replay

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La funzionalità Riesecuzione distribuita di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di valutare l'impatto dei futuri aggiornamenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile usarla anche per valutare l'impatto degli aggiornamenti hardware e del sistema operativo e dell'ottimizzazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="benefits-of-distributed-replay"></a>Vantaggi di Distributed Replay  
 Analogamente a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], è possibile utilizzare Distributed Replay per riprodurre una traccia acquisita su un ambiente di testing aggiornato. Diversamente da [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], Distributed Replay non si limita alla riproduzione del carico di lavoro da un singolo computer,  
  
 Distributed Replay offre una soluzione più scalabile rispetto a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Con Distributed Replay è possibile riprodurre un carico di lavoro da più computer e simulare in modo migliore un carico di lavoro di importanza critica.  
  
 La funzionalità Riesecuzione distribuita di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può usare più computer per riprodurre dati di traccia e simulare un carico di lavoro di importanza critica. Utilizzare Distributed Replay per testare la compatibilità delle applicazioni e le prestazioni o per pianificare la capacità.  
  
## <a name="when-to-use-distributed-replay"></a>Quando utilizzare Distributed Replay  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e Riesecuzione distribuita offrono alcune funzionalità sovrapposte.  
  
 È possibile utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per riprodurre una traccia acquisita su un ambiente di testing aggiornato. È inoltre possibile analizzare i risultati di riproduzione per cercare possibili incompatibilità funzionali e di prestazioni. Tuttavia, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] può riprodurre solo un carico di lavoro da un singolo computer. Quando si riproduce un'applicazione OLTP intensiva che ha molte connessioni simultanee attive o una velocità effettiva elevata, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] può costituire un collo di bottiglia per le risorse.  
  
 Distributed Replay offre una soluzione più scalabile rispetto a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Utilizzarlo per riprodurre un carico di lavoro da più computer e simulare in modo migliore un carico di lavoro di importanza critica.  
  
 Nella tabella seguente viene descritto quando utilizzare ciascuno strumento.  
  
|Strumento|Usare se...|  
|----------|---------------|  
|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]|Si desidera utilizzare il meccanismo di riproduzione convenzionale in un singolo computer. In particolare, sono necessarie funzionalità di debug riga per riga, ad esempio i comandi **Passaggio**, **Esegui fino al cursore**e **Imposta/Rimuovi punto di interruzione** .<br /><br /> Si desidera riprodurre una traccia per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|Distributed Replay|Si desidera valutare la compatibilità delle applicazioni. Si desidera, ad esempio, testare scenari di aggiornamento di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e del sistema operativo, gli aggiornamenti hardware o l'ottimizzazione degli indici.<br /><br /> La concorrenza nella traccia acquisita è talmente elevata che un singolo client di riproduzione non è in grado di simularla in modo appropriato.|  
  
## <a name="distributed-replay-concepts"></a>Concetti di base di Distributed Replay  
 I componenti seguenti costituiscono l'ambiente di Distributed Replay:  
  
-   **Strumento di amministrazione Riesecuzione distribuita**: applicazione console, **DReplay.exe**, usata per comunicare con il servizio controller di Riesecuzione distribuita. Utilizzare lo strumento di amministrazione per controllare la riproduzione distribuita.  
  
-   **Controller di Riesecuzione distribuita**: computer che esegue il servizio di Windows denominato controller di Riesecuzione distribuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Con il controller di Riesecuzione distribuita è possibile orchestrare le azioni dei client Riesecuzione distribuita. In ogni ambiente di Riesecuzione distribuita può essere presente una sola istanza del controller.  
  
-   **Client Riesecuzione distribuita**: uno o più computer (fisici o virtuali) che eseguono il servizio di Windows denominati client Riesecuzione distribuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I client Riesecuzione distribuita vengono usati insieme per simulare carichi di lavoro in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In ogni ambiente di Riesecuzione distribuita possono essere presenti uno o più client.  
  
-   **Server di destinazione**: istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che i client Riesecuzione distribuita possono usare per riprodurre i dati di traccia. È consigliabile posizionare il server di destinazione in un ambiente di testing.  
  
 Distributed Replay Administration Tool, Controller e Client possono essere installati in computer diversi o sullo stesso computer. Sullo stesso computer può essere in esecuzione una sola istanza del servizio Distributed Replay Controller o Client.  
  
 Nella figura seguente viene mostrata l'architettura fisica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay:  
  
 ![Architettura di Riesecuzione distribuita](../../tools/distributed-replay/media/distributedreplayarch.gif "Architettura di Riesecuzione distribuita")  
  
## <a name="distributed-replay-tasks"></a>Attività Distributed Replay  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene descritto come configurare Distributed Replay.|[Configurare Riesecuzione distribuita](../../tools/distributed-replay/configure-distributed-replay.md)|  
|Viene descritto come preparare i dati di traccia di input.|[Preparare i dati di traccia di input](../../tools/distributed-replay/prepare-the-input-trace-data.md)|  
|Viene descritto come riprodurre i dati di traccia.|[Rieseguire i dati di traccia](../../tools/distributed-replay/replay-trace-data.md)|  
|Viene descritto come rivedere i risultati dei dati di traccia di Distributed Replay.|[Esaminare i risultati della riesecuzione](../../tools/distributed-replay/review-the-replay-results.md)|  
|Viene descritto come usare lo strumento di amministrazione per avviare, monitorare e annullare operazioni nel controller.|[Opzioni della riga di comando dello strumento di amministrazione &#40;Utilità Riesecuzione distribuita&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Forum di SQL Server Distributed Replay](https://social.technet.microsoft.com/Forums/sl/sqldru/)   
 [Using Distributed Replay to Load Test Your SQL Server - Part 2](https://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx)  (Uso di Riesecuzione distribuita per testare il caricamento di SQL Server, seconda parte)  
 [Using Distributed Replay to Load Test Your SQL Server - Part 1](https://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx) (Uso di Riesecuzione distribuita per testare il caricamento di SQL Server, prima parte)  
  
  
