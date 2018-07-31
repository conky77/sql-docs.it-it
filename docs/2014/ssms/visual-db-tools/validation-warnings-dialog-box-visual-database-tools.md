---
title: Finestra di dialogo Avvisi di convalida (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65556
- vdt.dlgbox.validationwarnings
ms.assetid: fc76e234-ec9c-4a19-a65b-cb558ec8268e
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 202881aef2ae0fc8aa5daa4f01d625a9e2a26860
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214311"
---
# <a name="validation-warnings-dialog-box-visual-database-tools"></a>Finestra di dialogo Avvisi di convalida (Visual Database Tools)
  Questa finestra di dialogo viene visualizzata se si cerca di salvare modifiche che comportano conseguenze potenzialmente dannose o se l'operazione di commit sul database presenta molte probabilità di insuccesso. Indica quali potrebbero essere le conseguenze dannose o perché l'operazione di commit potrebbe non riuscire e consente di scegliere se procedere con la modifica o se annullare l'operazione.  
  
> [!NOTE]  
>  Questa finestra di dialogo viene visualizzata quando si tenta di trasmettere le modifiche al database o quando si salva uno script delle modifiche.  
  
 La finestra di dialogo può essere visualizzata per i seguenti motivi:  
  
-   Non si dispone delle autorizzazioni sul database per eseguire il commit di tutte le modifiche.  
  
-   Le modifiche danno come risultato colonne derivate generate in modo errato, vincoli predefiniti o vincoli CHECK.  
  
-   Una modifica al tipo di dati di una colonna potrebbe causare una perdita di dati.  
  
-   Una modifica porterebbe alla creazione di un indice più grande di 900 byte.  
  
-   Una modifica cambierebbe una tabella o una colonna che contribuisce a una vista associata a schema o una funzione definita dall'utente.  
  
-   Una modifica provocherebbe una nuova creazione di una tabella che ha uno o più trigger crittografati, con la conseguente eliminazione dei trigger.  
  
-   Le modifiche produrranno numerose assegnazioni di ANSI_NULLS o ANSI_PADDING o entrambi per le colonne all'interno di una tabella.  
  
## <a name="options"></a>Opzioni  
 **Sì**  
 Consente di procedere con l'operazione e generare lo script delle modifiche oppure di trasmettere le modifiche al database. È comunque possibile che si verifichino errori nell'operazione di commit, se non si dispone dei privilegi necessari per la modifica del database, se le modifiche comportano la creazione di un indice più grande di 900 byte oppure se le modifiche danno come risultato una colonna derivata generata in modo errato, un vincolo predefinito o un vincolo CHECK.  
  
 **No**  
 Annulla l'operazione di salvataggio.  
  
 **Salva file di testo**  
 Visualizza la finestra di dialogo **Salva con nome** , in cui è possibile specificare un percorso per un file di testo che include un elenco degli avvisi.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di tabelle &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  