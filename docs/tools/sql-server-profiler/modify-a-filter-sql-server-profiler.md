---
title: Modificare un filtro
titleSuffix: SQL Server Profiler
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 8b317813-4918-4485-b930-77b1951aa00c
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 4953da977f5172b8e861069616ff96e792dac8ff
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307179"
---
# <a name="modify-a-filter-sql-server-profiler"></a>Modificare un filtro (SQL Server Profiler)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Per limitare il numero di eventi raccolti da una traccia, è possibile aggiungere filtri ai modelli di traccia che contengono le definizioni di traccia. La limitazione del numero di eventi raccolti può ridurre gli effetti negativi delle operazioni di traccia sulle prestazioni. Se si impostano filtri per un modello di traccia e si rileva che il tipo di informazioni raccolte nella traccia non corrisponde a quello desiderato, è possibile modificare il filtro.  
  
### <a name="to-modify-a-filter"></a>Per modificare un filtro  
  
1.  In [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]aprire il modello del filtro di traccia da modificare. Scegliere **Modelli** dal menu **File**e quindi fare clic su **Modifica modello**.  
  
2.  Nella scheda **Generale** della finestra di dialogo **Proprietà modello di traccia** selezionare un modello nell'elenco **Seleziona nome modello** .  
  
3.  Fare clic sulla scheda **Selezione eventi** .  
  
     La scheda **Selezione eventi** contiene un controllo griglia, ovvero una tabella che include tutte le classi di evento tracciabili. La tabella contiene una riga per ogni classe di evento. Le classi di evento possono differire leggermente a seconda del tipo e della versione del server cui si è connessi. Le classi di eventi sono identificate nella colonna **Eventi**della griglia e sono raggruppate per categoria di eventi. Nelle altre colonne sono elencate le colonne di dati che possono essere restituite per ogni classe di evento.  
  
4.  Fare clic su **Filtri colonne**.  
  
5.  Nella finestra di dialogo **Modifica filtro** fare clic sul valore accanto all'operatore di confronto da modificare e digitare il nuovo valore oppure eliminarne uno. È inoltre possibile aggiungere ulteriori filtri.  
  
6.  Fare clic su **OK** e salvare il modello.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
