---
title: 'Avvio rapido: Strutture di dati, tipi di dati e oggetti R'
description: In questo argomento di avvio rapido si scoprirà come usare le strutture di dati, i tipi di dati e gli oggetti quando si usa R in Machine Learning Services per SQL Server. Si apprenderà come trasferire i dati tra R e SQL Server e verranno illustrati i problemi comuni che potrebbero verificarsi.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/27/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a3f978865d2fdd643650a7c7308adb65d2c79fa7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916409"
---
# <a name="quickstart-data-structures-data-types-and-objects-using-r-in-sql-server-machine-learning-services"></a>Avvio rapido: Strutture di dati, tipi di dati e oggetti quando si usa R in Machine Learning Services per SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In questo argomento di avvio rapido si scoprirà come usare le strutture di dati e i tipi di dati quando si usa R in Machine Learning Services per SQL Server. Si apprenderà come trasferire i dati tra R e SQL Server e verranno illustrati i problemi comuni che potrebbero verificarsi.

I problemi comuni da tenere in considerazione includono:

- Tipi di dati che talvolta non corrispondono
- Conversioni implicite che possono venire eseguite
- In alcuni casi sono necessarie operazioni cast e convert
- R e SQL usano oggetti dati differenti

## <a name="prerequisites"></a>Prerequisites

- Questo argomento di avvio rapido richiede l'accesso a un'istanza di SQL Server con [Machine Learning Services per SQL Server](../install/sql-machine-learning-services-windows-install.md) con il linguaggio R installato.

  L'istanza di SQL Server può essere in una macchina virtuale di Azure o in locale. Tenere presente che la funzionalità di scripting esterno è disabilitata per impostazione predefinita, quindi potrebbe essere necessario [abilitare lo scripting esterno](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) e verificare che il **servizio Launchpad di SQL Server** sia in esecuzione prima di iniziare.

- È anche necessario uno strumento per l'esecuzione di query SQL che contengono script R. È possibile eseguire questi script usando qualsiasi strumento di gestione del database o di query, purché possa connettersi a un'istanza di SQL Server, nonché eseguire una query T-SQL o una stored procedure. In questo argomento di avvio rapido viene usato [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="always-return-a-data-frame"></a>Restituire sempre un frame di dati

Quando lo script restituisce risultati da R a SQL Server, i dati devono essere restituiti come **data.frame**. Qualsiasi altro tipo di oggetto generato nello script (elenco, fattore, vettore o dati binari) deve essere convertito in un frame di dati se si vuole restituirlo come parte dei risultati della stored procedure. A questo scopo, sono disponibili più funzioni R per il supporto della modifica di altri oggetti in un frame di dati. È anche possibile serializzare un modello binario e restituirlo in un frame di dati, come si farà più avanti in questo argomento di avvio rapido.

Per prima cosa, si proverà a usare alcuni oggetti R di base, come vettori, matrici ed elenchi, per vedere in che modo la conversione in un frame di dati modifica l'output passato a SQL Server.

Confrontare questi due script "Hello World" in R. Il loro aspetto è quasi identico, ma il primo restituisce una singola colonna di tre valori, mentre il secondo restituisce tre colonne con un singolo valore ciascuna.

**Esempio 1**

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
     , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
     , @input_data_1 = N' ';
```

**Esempio 2**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' OutputDataSet<- data.frame(c("hello"), " ", c("world"));'
      , @input_data_1 = N'  ';
```

## <a name="identify-schema-and-data-types"></a>Identificare lo schema e i tipi di dati

Perché i risultati sono così diversi?

La risposta può essere trovata usando il comando `str()` di R. Aggiungere la funzione `str(object_name)` in qualsiasi punto dello script R per fare in modo che lo schema dati dell'oggetto R specificato venga restituito come messaggio informativo. Per visualizzare i messaggi, vedere il riquadro **Messaggi** di Visual Studio Code o la scheda **Messaggi** in SSMS.

Per capire come mai l'Esempio 1 e l'Esempio 2 producano risultati così diversi, inserire la riga `str(OutputDataSet)` alla fine della definizione di variabile _@script_ in ogni istruzione, come riportato di seguito:

**Esempio 1 con la funzione str aggiunta**

```sql
EXECUTE sp_execute_external_script
        @language = N'R'
      , @script = N' mytextvariable <- c("hello", " ", "world");
      OutputDataSet <- as.data.frame(mytextvariable);
      str(OutputDataSet);'
      , @input_data_1 = N'  '
;
```

**Esempio 2 con la funzione str aggiunta**

```sql
EXECUTE sp_execute_external_script
  @language = N'R', 
  @script = N' OutputDataSet <- data.frame(c("hello"), " ", c("world"));
    str(OutputDataSet);' , 
  @input_data_1 = N'  ';
```

A questo punto, riesaminare il testo in **Messaggi** per capire perché l'output è differente.

**Risultati - Esempio 1**

```sql
STDOUT message(s) from external script:
'data.frame':   3 obs. of  1 variable:
$ mytextvariable: Factor w/ 3 levels " ","hello","world": 2 1 3
```

**Risultati - Esempio 2**

```sql
STDOUT message(s) from external script:
'data.frame':   1 obs. of  3 variables:
$ c..hello..: Factor w/ 1 level "hello": 1
$ X...      : Factor w/ 1 level " ": 1
$ c..world..: Factor w/ 1 level "world": 1
```

Come si può notare, una leggera modifica nella sintassi di R ha un effetto notevole sullo schema dei risultati. Non verranno esaminati in dettaglio i motivi, ma le differenze tra i tipi di dati R sono descritte in modo più approfondito nella sezione sulle *strutture dei dati* del documento ["Advanced R" di Hadley Wickham](http://adv-r.had.co.nz).

Per il momento, tenere semplicemente presente che è necessario verificare i risultati previsti quando si convertono oggetti R in frame di dati.

> [!TIP]
> È anche possibile usare funzioni di identità R, ad esempio `is.matrix`, `is.vector`, per restituire informazioni sulla struttura dei dati interna.

## <a name="implicit-conversion-of-data-objects"></a>Conversione implicita di oggetti dati

Ogni oggetto dati R ha regole specifiche per la gestione dei valori in combinazione con altri oggetti dati se i due oggetti dati hanno lo stesso numero di dimensioni o se un oggetto dati contiene tipi di dati eterogenei.

Creare prima di tutto una piccola tabella di dati di test.

```sql
CREATE TABLE RTestData (col1 INT NOT NULL)

INSERT INTO RTestData
VALUES (1);

INSERT INTO RTestData
VALUES (10);

INSERT INTO RTestData
VALUES (100);
GO
```

Si supponga ad esempio di eseguire l'istruzione seguente per portare a termine una moltiplicazione di oggetti matrix usando R. Si moltiplica un oggetto matrix a colonna singola con tre valori per un oggetto array con quattro valori e si prevede di ottenere come risultato un oggetto matrix 4x3.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:15);
    OutputDataSet <- as.data.frame(x %*% y);'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (([Col1] int, [Col2] int, [Col3] int, Col4 int));
```

La colonna di tre valori viene convertita automaticamente in un oggetto matrix a colonna singola. Poiché un oggetto matrix è semplicemente un caso speciale di oggetto array in R, l'oggetto array `y` viene convertito in modo implicito in un oggetto matrix a colonna singola per rendere conformi i due argomenti.

**Risultati**

|Col1|Col2|Col3|Col4|
|---|---|---|---|
|12|13|14|15|
|120|130|140|150|
|1200|1300|1400|1500|

Si noti tuttavia cosa accade se si modificano le dimensioni dell'oggetto array `y`.

```sql
execute sp_execute_external_script
   @language = N'R'
   , @script = N'
        x <- as.matrix(InputDataSet);
        y <- array(12:14);
   OutputDataSet <- as.data.frame(y %*% x);'
   , @input_data_1 = N' SELECT [Col1]  from RTestData;'
   WITH RESULT SETS (([Col1] int ));
```

Adesso R restituisce come risultato un valore singolo.

**Risultati**

|Col1|
|---|
|1542|

Perché? In questo caso, dal momento che i due argomenti possono essere gestiti come vettori della stessa lunghezza, R restituisce il prodotto interno come oggetto matrix.  Questo è il comportamento previsto in base alle regole dell'algebra lineare; tuttavia, potrebbe causare problemi se l'applicazione downstream prevede che lo schema di output non venga mai modificato.

> [!TIP]
> 
> Si verificano errori? Verificare che la stored procedure sia in esecuzione nel contesto del database che contiene la tabella e non nel database **master** o in un altro database.
>
> Si consiglia inoltre di evitare l'uso di tabelle temporanee per questi esempi. Alcuni client R terminano la connessione tra i batch, eliminando le tabelle temporanee.

## <a name="merge-or-multiply-columns-of-different-length"></a>Unire o moltiplicare colonne di lunghezza diversa

R offre una notevole flessibilità per l'uso di vettori di dimensioni diverse e per la combinazione di queste strutture di tipo colonna nei frame di dati. Gli elenchi dei vettori sono simili a una tabella, ma non seguono tutte le regole delle tabelle del database.

Ad esempio, lo script seguente definisce un oggetto array numerico di lunghezza 6 e lo archivia nella variabile R `df1`. L'oggetto array numerico viene quindi combinato con i numeri interi della tabella RTestData, che contiene tre (3) valori, per creare un nuovo frame di dati `df2`.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
    , @script = N'
               df1 <- as.data.frame( array(1:6) );
               df2 <- as.data.frame( c( InputDataSet , df1 ));
               OutputDataSet <- df2'
    , @input_data_1 = N' SELECT [Col1]  from RTestData;'
    WITH RESULT SETS (( [Col2] int not null, [Col3] int not null ));
```

Per riempire il frame di dati, R ripete gli elementi recuperati da RTestData per il numero di volte necessario per corrispondere al numero di elementi nell'oggetto array `df1`.

**Risultati**

|*Col2*|*Col3*|
|----|----|
|1|1|
|10|2|
|100|3|
|1|4|
|10|5|
|100|6|

Ricordare che un frame di dati ha solo l'aspetto di una tabella, ma in realtà è un elenco di vettori.

## <a name="cast-or-convert-sql-server-data"></a>Eseguire il cast o convertire i dati di SQL Server

R e SQL Server non usano gli stessi tipi di dati, pertanto quando si esegue una query in SQL Server per ottenere i dati e quindi passarli al runtime di R, viene in genere eseguita una sorta di conversione implicita. Un'altra serie di conversioni ha luogo quando si restituiscono i dati da R a SQL Server.

- SQL Server esegue il push dei dati ricevuti dalla query nel processo R gestito dal servizio Launchpad e li converte in una rappresentazione interna per offrire maggiore efficienza.
- Il runtime R carica i dati in una variabile data.frame ed esegue a sua volta operazioni sui dati.
- Il motore di database restituisce i dati a SQL Server usando una connessione interna protetta e presenta i dati in termini di tipi di dati di SQL Server.
- I dati vengono ottenuti tramite la connessione a SQL Server con una libreria client o di rete in grado di eseguire query SQL e di gestire set di dati tabulari. Questa applicazione client può influire sui dati in altri modi.

Per visualizzarne il funzionamento, eseguire una query come questa sul data warehouse [AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Questa vista restituisce i dati di vendita usati per la creazione delle previsioni.

```sql
USE AdventureWorksDW
GO

SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = 'M200 Europe'
           ORDER BY ReportingDate ASC
```

> [!NOTE]
>
> È possibile usare qualsiasi versione di AdventureWorks o creare una query diversa usando un database personalizzato. L'importante è provare a gestire alcuni dati contenenti valori numerici, di testo e di data/ora.

Provare quindi a incollare questa query come input per la stored procedure.

```sql
EXECUTE sp_execute_external_script
       @language = N'R'
      , @script = N' str(InputDataSet);
      OutputDataSet <- InputDataSet;'
      , @input_data_1 = N'
           SELECT ReportingDate
         , CAST(ModelRegion as varchar(50)) as ProductSeries
         , Amount
           FROM [AdventureWorksDW].[dbo].[vTimeSeries]
           WHERE [ModelRegion] = ''M200 Europe''
           ORDER BY ReportingDate ASC ;'
WITH RESULT SETS undefined;
```

Se si verifica un errore, probabilmente sarà necessario apportare alcune modifiche al testo della query. Ad esempio, il predicato stringa nella clausola WHERE deve essere racchiuso tra due set di virgolette singole.

Dopo avere verificato che la query funzioni, esaminare i risultati della funzione `str` per visualizzare la modalità di gestione dei dati di input in R.

**Risultati**

```sql
STDOUT message(s) from external script: 'data.frame':    37 obs. of  3 variables:
STDOUT message(s) from external script: $ ReportingDate: POSIXct, format: "2010-12-24 23:00:00" "2010-12-24 23:00:00"
STDOUT message(s) from external script: $ ProductSeries: Factor w/ 1 levels "M200 Europe",..: 1 1 1 1 1 1 1 1 1 1
STDOUT message(s) from external script: $ Amount       : num  3400 16925 20350 16950 16950
```

- La colonna datetime è stata elaborata usando il tipo di dati R **POSIXct**.
- La colonna di testo "ProductSeries" è stata identificata come **fattore**, vale a dire una variabile di categoria. Per impostazione predefinita, i valori stringa sono gestiti come fattori. Se si passa una stringa a R, viene convertita in un numero intero per uso interno e quindi rimappata alla stringa nell'output.

### <a name="summary"></a>Summary

Da questi brevi esempi è possibile capire la necessità di controllare gli effetti della conversione dei dati quando si passano query SQL come input. Poiché alcuni tipi di dati di SQL Server non sono supportati da R, tenere in considerazione questi suggerimenti per evitare errori:

- Testare i dati in anticipo e verificare le colonne o i valori nello schema che potrebbero creare problemi quando vengono passati al codice R.
- Specificare le colonne nell'origine dati di input singolarmente, anziché usare `SELECT *`, per vedere in che modo verrà gestita ogni colonna.
- Quando si preparano i dati di input, eseguire cast espliciti in base alle necessità per evitare sorprese.
- Evitare di passare colonne di dati, ad esempio GUID o RowGuid, che provocano errori e che non sono utili per la modellazione.

Per altre informazioni sui tipi di dati supportati e non supportati, vedere [Librerie e tipi di dati R](../r/r-libraries-and-data-types.md).

Per informazioni sull'impatto sulle prestazioni della conversione in fase di esecuzione delle stringhe in fattori numerici, vedere [Ottimizzazione delle prestazioni di R Services per SQL Server](../r/sql-server-r-services-performance-tuning.md).

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sulla scrittura di funzioni R avanzate in SQL Server, vedere questo argomento di avvio rapido:

> [!div class="nextstepaction"]
> [Scrivere funzioni R avanzate con Machine Learning Services per SQL Server](quickstart-r-functions.md)

Per altre informazioni sull'uso di R in Machine Learning Services per SQL Server, vedere gli articoli seguenti:

- [Creare un modello predittivo e assegnare punteggi in R con Machine Learning Services per SQL Server](quickstart-r-train-score-model.md)
- [Che cos'è Machine Learning Services per SQL Server (Python e R)?](../what-is-sql-server-machine-learning.md)
