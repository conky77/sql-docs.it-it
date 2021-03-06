---
title: 'Esercitazione: Strumento Ottimizzazione guidata motore di database'
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], tutorials
- tutorials [Database Engine Tuning Advisor]
ms.assetid: 3b54cbbe-d8c6-424d-92f1-aa58179f4da8
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: a6fea0bbb9c9471885f76f3f6f44a86b50718d3e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "75304701"
---
# <a name="tutorial-database-engine-tuning-advisor"></a>Esercitazione: Strumento Ottimizzazione guidata motore di database

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In questa esercitazione verrà illustrata Ottimizzazione guidata motore di database che esamina il modo in cui vengono elaborate le query nei database specificati e offre indicazioni su come migliorare le prestazioni di elaborazione attraverso la modifica delle strutture di database, ad esempio indici, viste indicizzate e partizionamento.  
  
Ottimizzazione guidata motore di database ha due interfacce utente, vale a dire un'interfaccia utente grafica (GUI) e l'utilità del prompt dei comandi **dta** . L'interfaccia utente grafica consente di visualizzare rapidamente i risultati delle sessioni di ottimizzazione, mentre con l'utilità **dta** è possibile incorporare con semplicità la funzionalità dello strumento Ottimizzazione guidata motore di database in script per l'ottimizzazione automatica. Lo strumento Ottimizzazione guidata motore di database, inoltre, può utilizzare input in formato XML, che garantisce un maggiore controllo sul processo di ottimizzazione.  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
In questa esercitazione verrà illustrato come navigare nell'interfaccia utente grafica dello strumento Ottimizzazione guidata motore di database ed eseguire alcune semplici attività usando sia la GUI che l'utilità **dta** . Questa esercitazione contiene le lezioni seguenti:  
  
[Lezione 1: Navigazione di base in Ottimizzazione guidata motore di database](../../tools/dta/lesson-1-basic-navigation-in-database-engine-tuning-advisor.md)  
In questa lezione sarà possibile acquisire familiarità con la GUI dello strumento Ottimizzazione guidata motore di database e ottenere informazioni su come impostare il layout e le opzioni di visualizzazione.  
  
[Lezione 2: Uso dello strumento Ottimizzazione guidata motore di database](../../tools/dta/lesson-2-using-database-engine-tuning-advisor.md)  
In questa lezione verranno descritte le procedure per eseguire alcune semplici attività di ottimizzazione utilizzando la GUI dello strumento Ottimizzazione guidata motore di database.  
  
[Lezione 3: Uso dell'utilità del prompt dei comandi dta](../../tools/dta/lesson-3-using-the-dta-command-prompt-utility.md)  
In questa lezione verranno descritte le procedure per avviare l'utilità del prompt dei comandi **dta** e per eseguire alcune semplici comandi per l'ottimizzazione.  
  
## <a name="requirements"></a>Requisiti  
Questa esercitazione è destinata agli amministratori di database che non hanno familiarità con l'interfaccia utente grafica dello strumento Ottimizzazione guidata motore di database o con l'utilità del prompt dei comandi **dta** , ma che hanno tuttavia esperienza in merito ai concetti e alle strutture relativi ai database, quali indici e viste indicizzate.  
  
È necessario installare [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , o una versione successiva, con i database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Per una maggiore sicurezza, i database di esempio non vengono installati per impostazione predefinita. Per installare i database di esempio, vedere la pagina [Installazione degli esempi e dei database di esempio di SQL Server](https://sqlserversamples.codeplex.com).  
  
## <a name="after-you-finish-this-tutorial"></a>Al termine di questa esercitazione  
Al termine di questa esercitazione, per ulteriori informazioni sullo strumento Ottimizzazione guidata motore di database, è possibile consultare gli argomenti seguenti:  
  
-   [Ottimizzazione guidata motore di database](../../relational-databases/performance/database-engine-tuning-advisor.md) per le descrizioni sull'uso di questo strumento in determinate attività.  
  
-   [Utilità dta](../../tools/dta/dta-utility.md) per materiale di riferimento sull'utilità del prompt dei comandi e sul file XML facoltativo disponibile per usare l'utilità.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 1: Navigazione di base in Ottimizzazione guidata motore di database](../../tools/dta/lesson-1-basic-navigation-in-database-engine-tuning-advisor.md)  
  
  
  
