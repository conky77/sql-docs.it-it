---
title: Elimina oggetti
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 91ff60508e0c22ae202cd6984b5c8d5ad84cc879
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "75257205"
---
# <a name="delete-objects"></a>Elimina oggetti
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Utilizzare questa finestra di dialogo per eliminare un database o un oggetto di database.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
**Oggetto da eliminare**  
Consente di visualizzare i nomi, i tipi, i proprietari e lo stato degli oggetti da eliminare, nonché gli eventuali messaggi relativi agli errori verificatisi durante l'esecuzione.  
  
> [!NOTE]  
> L'esecuzione dell'opzione **Elimina** su un database equivale all'esecuzione di DROP DATABASE in [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**Mostra dipendenze**  
Fare clic su questo pulsante per visualizzare sia gli oggetti che dipendono dall'oggetto attualmente selezionato che gli oggetti dal quale dipende l'oggetto corrente (dipendenza verso l'alto e verso il basso). Le informazioni visualizzate nella finestra di dialogo **Mostra dipendenze** sono di sola lettura.  
  
> [!NOTE]  
> Il pulsante **Mostra dipendenze** non viene visualizzato per tutti i tipi di oggetti di database. Per visualizzare le dipendenze quando il pulsante **Mostra dipendenze** non è disponibile, fare clic sull'oggetto con il pulsante destro del mouse in Esplora oggetti e scegliere **Visualizza dipendenze**.  
  
**Elimina informazioni di cronologia di backup e ripristino per i database**  
Questa casella di controllo viene visualizzata solo quando viene eliminato un database e comporta l'eliminazione dal database **msdb** della cronologia di backup e ripristino del database eliminato.  
  
**Chiudi connessioni esistenti**  
Questa casella di controllo viene visualizzata solo quando viene eliminato un database e interrompe le connessioni al database eliminato.  
  
