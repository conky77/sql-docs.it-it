---
title: Creare query di accodamento valori (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting values
- queries [SQL Server], types
- adding values
- row additions [SQL Server], Insert Values query
- inserting rows
- Insert Values query
- adding rows
- table values [SQL Server]
ms.assetid: 2d4b2f6d-cc09-434b-8a0e-ccce40628064
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 019c2fe96be00c6e86e0c94286770d30e7a54a9c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62676333"
---
# <a name="create-insert-values-queries-visual-database-tools"></a>Creazione di query di accodamento valori (Visual Database Tools)
  Per creare una nuova riga nella tabella corrente, è possibile utilizzare una query di accodamento valori. Durante la creazione di una query di accodamento valori è necessario specificare:  
  
-   la tabella di database a cui aggiungere la riga  
  
-   le colonne di cui si desidera aggiungere il contenuto  
  
-   il valore o l'espressione da inserire nelle singole colonne.  
  
 Ad esempio, la seguente query aggiunge una riga alla tabella `titles` , specificando i valori relativi al titolo, al tipo, all'editore e al prezzo:  
  
```  
INSERT INTO titles  
         (title_id, title, type, pub_id, price)  
VALUES   ('BU9876', 'Creating Web Pages', 'business', '1389', '29.99')  
```  
  
 Quando si crea una query di accodamento valori, nel riquadro Criteri vengono visualizzate solo le opzioni disponibili per l'inserimento di una nuova riga, ovvero il nome della colonna e il valore da inserire.  
  
> [!CAUTION]  
>  Una volta eseguita, la query di accodamento valori non potrà essere annullata. È dunque opportuno eseguire una copia di backup dei dati prima di eseguire la query.  
  
### <a name="to-create-an-insert-values-query"></a>Per creare una query di accodamento valori  
  
1.  Aggiungere al riquadro Diagramma la tabella da aggiornare.  
  
2.  Scegliere **Modifica tipo** dal menu **Progettazione query**e **Accodamento valori**.  
  
    > [!NOTE]  
    >  Se nel riquadro diagramma è visualizzata più di una tabella quando si avvia la query di accodamento valori, in Progettazione query e Progettazione viste verrà visualizzata la [finestra di dialogo Scegliere la tabella di destinazione per Accodamento valori](visual-database-tools.md) , in cui sarà possibile specificare il nome della tabella da aggiornare.  
  
3.  Nel riquadro Diagramma selezionare le caselle di controllo relative alle colonne per cui si desidera specificare nuovi valori. Queste colonne verranno visualizzate nel riquadro Criteri. Verranno aggiornate solo le colonne aggiunte alla query.  
  
4.  Nella colonna **Nuovo valore** del riquadro Criteri immettere il nuovo valore per la colonna. È possibile immettere valori letterali, nomi di colonna o espressioni. Il valore deve corrispondere o essere compatibile con il tipo di dati della colonna da aggiornare.  
  
    > [!CAUTION]  
    >  In Progettazione query e Progettazione viste non è possibile verificare la compatibilità di un valore rispetto alla lunghezza della colonna di inserimento. Se il valore inserito è troppo lungo, è possibile che venga troncato senza preavviso. Ad esempio, se una colonna `name` è lunga 20 caratteri ma si specifica un valore di inserimento di 25 caratteri, è possibile che gli ultimi 5 caratteri vengano troncati.  
  
 Quando si esegue una query di accodamento valori, non viene restituito alcun risultato nel [riquadro Risultati](results-pane-visual-database-tools.md). Viene invece visualizzato un messaggio che indica il numero di righe modificate.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di query supportati &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md)   
 [Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Eseguire operazioni di base con le query &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
