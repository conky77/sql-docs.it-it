---
title: Libreria MicrosoftML di funzioni R
description: Introduzione alla libreria di funzioni MicrosoftML in R Services per SQL Server 2016 e in Machine Learning Services per SQL Server con R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 450091bba39cf10e551b8da5e62993ca676c64af
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "73707918"
---
# <a name="microsoftml-r-library-in-sql-server"></a>MicrosoftML (libreria R in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**MicrosoftML** è una libreria di funzioni R di Microsoft che fornisce algoritmi di Machine Learning a prestazioni elevate. Include funzioni per il training e le trasformazioni, l'assegnazione dei punteggi, l'analisi di testo e immagini e l'estrazione di caratteristiche per la derivazione di valori da dati esistenti.

Le API di Machine Learning sono state sviluppate da Microsoft per le applicazioni di Machine Learning interne e sono state perfezionate nel corso degli anni per supportare prestazioni elevate per i Big Data, usando l'elaborazione multicore e il flusso dei dati rapido. MicrosoftML include anche numerose trasformazioni per l'elaborazione di testo e immagini.

## <a name="full-reference-documentation"></a>Documentazione di riferimento completa

La libreria **MicrosoftML** è distribuita in più prodotti Microsoft, ma l'utilizzo è lo stesso indipendentemente dal fatto che sia inclusa in SQL Server o in un altro prodotto. Poiché le funzioni sono le stesse, la [documentazione per le singole funzioni RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) viene pubblicata in una sola posizione nelle [informazioni di riferimento per R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) per Microsoft Machine Learning Server. In caso di comportamenti specifici per un prodotto, le discrepanze verranno indicate nella pagina della Guida delle funzioni in questione.

## <a name="versions-and-platforms"></a>Versioni e piattaforme

La libreria **MicrosoftML** è basata su R 3.4.3 ed è disponibile solo quando si installa uno dei prodotti o download Microsoft seguenti:

+ [R Services per SQL Server 2016](../install/sql-r-services-windows-install.md)
+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 o versione successiva](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R Client](set-up-a-data-science-client.md)

> [!NOTE]
> Le versioni complete del prodotto sono solo per Windows in SQL Server 2017. Sia Windows che Linux sono supportati per **MicrosoftML** in [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md).

## <a name="package-dependencies"></a>Dipendenze dei pacchetti

Gli algoritmi in **MicrosoftML** dipendono da [RevoScaleR](ref-r-revoscaler.md) per:

+ Oggetti di origine dati. I dati utilizzati dalle funzioni di **MicrosoftML** vengono creati usando le funzioni di **RevoScaleR**.
+ Elaborazione remota (spostamento dell'esecuzione delle funzioni in un'istanza di SQL Server remota). La libreria **RevoScaleR** fornisce funzioni per la creazione e l'attivazione di un contesto di calcolo remoto per SQL Server.

Nella maggior parte dei casi, i pacchetti vengono caricati insieme ogni volta che si usa **MicrosoftML**.

## <a name="functions-by-category"></a>Funzioni per categoria

Questa sezione elenca le funzioni per categoria per offrire un'idea di come vengono usate. È anche possibile usare il [sommario](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) per trovare le funzioni in ordine alfabetico.

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1 - Algoritmi di Machine Learning

| Nome della funzione | Descrizione |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | Implementazione di FastRank, un'implementazione efficiente dell'algoritmo di gradient boosting MART.  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Implementazione della foresta casuale e della foresta di regressione quantile tramite [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees).  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Regressione logistica tramite L-BFGS.  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | Macchine a vettori di supporto a una classe.  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | Rete neurale di regressione binaria multiclasse.  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | Ottimizzazione SDCA (Stochastic Dual Coordinate Ascent) per la regressione e la classificazione binaria lineari. |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | Esegue il training di numerosi modelli di vario tipo per ottenere prestazioni predittive migliori rispetto a quelle ottenute da un singolo modello.|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2 - Funzioni di trasformazione

| Nome della funzione | Descrizione |
|---------------|-------------|
|[concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | Trasformazione per creare una singola colonna con valori di vettore da più colonne.  |
|[categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | Creare il vettore indicatore usando la trasformazione categorica con il dizionario.  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | Converte il valore categorico in una matrice di indicatori tramite hashing. |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | Produce un contenitore di conteggi di sequenze di parole consecutive, denominate n-grammi, da un determinato corpus di testo. Offre rilevamento della lingua, tokenizzazione, rimozione di parole non significative, normalizzazione del testo e generazione di caratteristiche.  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | Assegna un punteggio al testo in linguaggio naturale e crea una colonna contenente le probabilità che i sentiment nel testo siano positivi.|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | Consente di definire argomenti per l'estrazione di caratteristiche basate su conteggi e su hash.|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | Seleziona un set di colonne di cui ripetere il training, eliminando tutte le altre. |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | Seleziona le caratteristiche delle variabili specificate usando una modalità specificata.|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | Carica i dati dell'immagine.|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | Ridimensiona un'immagine a una dimensione specificata usando un metodo di ridimensionamento specificato.|
|[extractPixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | Estrae i valori pixel da un'immagine.|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | Definisce le caratteristiche di un'immagine usando un modello di rete neurale profonda con training preliminare.|


## <a name="3-scoring-and-training-functions"></a>3 - Funzioni di assegnazione dei punteggi e training

| Nome della funzione | Descrizione |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | Esegue la libreria di punteggi da SQL Server, usando la stored procedure, o dal codice R abilitando il punteggio in tempo reale per offrire prestazioni della stima molto più veloci.|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | Trasforma i dati da un set di dati di input a un set di dati di output.|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Fornisce un riepilogo di un modello di Machine Learning di Microsoft R.|


## <a name="4-loss-functions-for-classification-and-regression"></a>4 - Funzioni di perdita per la regressione e la classificazione

| Nome della funzione | Descrizione |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Specifiche per la funzione di perdita per la classificazione esponenziale. | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Specifiche per la funzione di perdita per la classificazione dei log.  |
|[hingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Specifiche per la funzione di perdita per la classificazione cardine. | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Specifiche per la funzione di perdita per la classificazione cardine liscia.  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Specifiche per la funzione di perdita di regressione di Poisson. | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | Specifiche per la funzione di perdita di regressione al quadrato.   |   

## <a name="5-feature-selection-functions"></a>5 - Funzioni di selezione delle caratteristiche

| Nome della funzione | Descrizione |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | Specifica per la selezione delle caratteristiche in modalità di conteggio. |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | Specifica per la selezione delle caratteristiche in modalità di informazione mutua. |

## <a name="6-ensemble-modeling-functions"></a>6 - Funzioni di modellazione di ensemble

| Nome della funzione | Descrizione |
|---------------|-------------|
|[fastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | Crea un elenco contenente il nome della funzione e gli argomenti per eseguire il training di un modello Fast Tree con [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | Crea un elenco contenente il nome della funzione e gli argomenti per eseguire il training di un modello Fast Forest con [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | Crea un elenco contenente il nome della funzione e gli argomenti per eseguire il training di un modello Fast Linear con [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | Crea un elenco contenente il nome della funzione e gli argomenti per eseguire il training di un modello di regressione logistica con [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | Crea un elenco contenente il nome della funzione e gli argomenti per eseguire il training di un modello OneClassSvm con [rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble).|

## <a name="7-neural-networking-functions"></a>7 - Funzioni di rete neurale

| Nome della funzione | Descrizione |
|---------------|-------------|
|[optimizer](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | Specifica gli algoritmi di ottimizzazione per l'algoritmo di Machine Learning [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet).|


## <a name="8-package-state-functions"></a>8 - Funzioni di stato del pacchetto

| Nome della funzione | Descrizione |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | Oggetto ambiente usato per archiviare lo stato a livello di pacchetto. |


## <a name="how-to-use-microsoftml"></a>Come usare MicrosoftML

Le funzioni in **MicrosoftML** possono essere chiamate nel codice R incapsulato nelle stored procedure. La maggior parte degli sviluppatori compila in locale le soluzioni **MicrosoftML** e quindi esegue la migrazione del codice R completato alle stored procedure, come esercizio di distribuzione.

Il pacchetto **MicrosoftML** per R è già installato in SQL Server 2017. È anche disponibile per l'uso con SQL Server 2016 se si aggiornano i componenti R per l'istanza: [Aggiornare un'istanza di SQL Server usando l'associazione](../install/upgrade-r-and-python.md)

Il pacchetto non è caricato per impostazione predefinita. Per prima cosa, caricare il pacchetto **MicrosoftML** e quindi caricare **RevoScaleR** se è necessario usare contesti di calcolo remoti oppure oggetti di origine dati o connettività correlati. Fare quindi riferimento alle singole funzioni necessarie.

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>Vedere anche

+ [Esercitazioni di R](../tutorials/sql-server-r-tutorials.md)
+ [Informazioni su come usare i contesti di calcolo](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R per sviluppatori SQL: eseguire il training e rendere operativo un modello](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Microsoft product samples on GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples) (Esempi di prodotti Microsoft in GitHub)
+ [Informazioni di riferimento su R (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 