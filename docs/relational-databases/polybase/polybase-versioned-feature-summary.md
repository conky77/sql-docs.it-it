---
title: Funzionalità e limitazioni di PolyBase | Microsoft Docs
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bd4c7e7bb150a0eafbd855e1703713f3781bdc49
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "71710450"
---
# <a name="polybase-features-and-limitations"></a>Funzionalità e limitazioni di PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

Questo articolo rappresenta un riepilogo delle funzionalità di PolyBase disponibili per i prodotti e servizi di SQL Server.  
  
## <a name="feature-summary-for-product-releases"></a>Riepilogo delle funzionalità per le versioni dei prodotti

Questa tabella elenca le funzionalità principali per PolyBase e i prodotti in cui sono disponibili.  
  
||||||
|-|-|-|-|-|   
|**Funzionalità**|**SQL Server 2016**|**Database SQL di Azure**|**Azure SQL Data Warehouse**|**Parallel Data Warehouse**| 
|Eseguire query sui dati di Hadoop con [!INCLUDE[tsql](../../includes/tsql-md.md)]|Sì|No|No|Sì|
|Importare dati da Hadoop|Sì|No|No|Sì|
|Esportare dati in Hadoop  |Sì|No|No| Sì|
|Eseguire query, importare da Azure HDInsight |No|No|No|No
|Eseguire il push down dei calcoli delle query in Hadoop|Sì|No|No|Sì|  
|Importare dati dall'archivio BLOB di Azure|Sì|No|Sì|Sì| 
|Esportare dati nell'archivio BLOB di Azure|Sì|No|Sì|Sì|  
|Importare dati da Azure Data Lake Store|No|No|Sì|No|    
|Esportare dati da Azure Data Lake Store|No|No|Sì|No|
|Eseguire query PolyBase da strumenti BI di Microsoft|Sì|No|Sì|Sì|   

## <a name="pushdown-computation-supported-by-t-sql-operators"></a>Calcolo della distribuzione dinamica supportata da operatori T-SQL

In SQL Server e APS, non tutti gli operatori T-SQL possono essere distribuiti sul cluster Hadoop. Nella tabella seguente sono elencati tutti gli operatori supportati e un subset degli operatori non supportati. 

||||
|-|-|-| 
|**Tipo di operatore**|**Distribuibile su hadoop**|**Distribuibile nell'archiviazione BLOB**|
|Proiezioni di colonna|Sì|No|
|Predicati|Sì|No|
|Aggregazioni|Parziale|No|
|Crea un join tra le tabelle esterne|No|No|
|Crea un join tra le tabelle esterne e locali|No|No|
|Ordina|No|No|

Aggregazione parziale significa che deve verificarsi un'aggregazione finale dopo che i dati raggiungono SQL Server. Tuttavia, una parte dell'aggregazione viene eseguita in Hadoop. Si tratta di un metodo comune di calcolo delle aggregazioni nei sistemi con la funzionalità di elaborazione parallela massiva.  

## <a name="known-limitations"></a>Limitazioni note

PolyBase include le limitazioni seguenti:

- Per usare PolyBase, sono necessarie le autorizzazioni a livello di CONTROLLO SERVER o sysadmin per il database.

- Le dimensioni massime consentite per la riga, inclusa la lunghezza totale delle colonne di lunghezza variabile, non possono superare 32 kB in SQL Server o 1 MB in Azure SQL Data Warehouse.

- Quando si esportano dati in un formato file ORC da SQL Server o SQL Data Warehouse, le colonne con grandi quantità di testo potrebbero essere limitate. Possono essere limitate a 50 colonne a causa di messaggi di errore di memoria insufficiente di Java. Per risolvere questo problema, esportare solo un subset delle colonne.

- PolyBase non può connettersi a un'istanza di Hortonworks se Knox è abilitata.

- Se si usano tabelle Hive con transactional=true, PolyBase non può accedere ai dati nella directory della tabella Hive.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase non viene installato quando si aggiunge un nodo a un cluster di failover di SQL Server 2016](https://support.microsoft.com/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster).

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su PolyBase, vedere [Che cos'è PolyBase?](polybase-guide.md).
