---
title: Cenni preliminari su schemi e dati multidimensionali | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- multidimensional schemas and data
ms.assetid: ce37fa06-c581-4d80-9a9b-c3aa66408909
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e4681bb9e1fd1028ee1ddc2bd7f72efc03fb6c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923183"
---
# <a name="overview-of-multidimensional-schemas-and-data"></a>Panoramica di schemi e dati multidimensionali
## <a name="understanding-multidimensional-schemas"></a>Informazioni sugli schemi multidimensionali  
 L'oggetto di metadati centrale in ADO MD è il *cubo*, costituito da un set strutturato di dimensioni, gerarchie, livelli e membri correlati.  
  
 Una *dimensione* è una categoria indipendente di dati del database multidimensionale, derivata dalle entità business. Una dimensione contiene in genere gli elementi da utilizzare come criteri di query per le misure del database.  
  
 Una *gerarchia* è un percorso di aggregazione di una dimensione. Una dimensione può avere più livelli di granularità, che hanno relazioni padre-figlio. Una gerarchia definisce la modalità di correlazione di questi livelli.  
  
 Un *livello* è un passaggio dell'aggregazione in una gerarchia. Per le dimensioni con più livelli di informazioni, ogni livello è un livello.  
  
 Un *membro* è un elemento di dati in una dimensione. In genere, è possibile creare una didascalia o descrivere una misura del database usando i membri.  
  
 I cubi sono rappresentati da oggetti [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) in ADO MD. Dimensioni, gerarchie, livelli e membri sono rappresentati anche dagli oggetti ADO MD corrispondenti, ovvero [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [Hierarchy](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)e [member](../../../ado/reference/ado-md-api/member-object-ado-md.md).  
  
### <a name="dimensions"></a>Dimensioni  
 Le dimensioni di un cubo dipendono dalle entità aziendali e dai tipi di dati da modellare nel database. In genere, ogni dimensione è un punto di ingresso o un meccanismo indipendente per la selezione dei dati.  
  
 Ad esempio, un cubo contenente i dati di vendita presenta le cinque dimensioni seguenti: venditore, geografia, ora, prodotti e misure. La dimensione Measures contiene i valori dei dati di vendita effettivi, mentre le altre dimensioni rappresentano modi per categorizzare e raggruppare i valori dei dati delle vendite.  
  
 Il set di membri della dimensione Geography è il seguente:  
  
```console
{All, North America, Europe, Canada, USA, UK, Germany, Canada-West,  
Canada-East, USA-NW, USA-SW, USA-NE, USA-SE, England, Scotland,   
Wales,Ireland, Germany-North, Germany-South, Ottawa, Toronto,   
Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston,   
Shreveport, Miami, Boston, New York, London, Dover, Glasgow,   
Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin,   
Hamburg, Munich, Stuttgart}  
```  
  
### <a name="hierarchies"></a>Gerarchie  
 Le gerarchie definiscono le modalità di rollup o raggruppamento dei livelli di una dimensione. Una dimensione può avere più di una gerarchia. Nella dimensione Geography esiste una gerarchia naturale:  
  
### <a name="levels"></a>Levels  
 Nella dimensione Geography di esempio illustrata nella figura precedente, ogni casella rappresenta un livello nella gerarchia.  
  
 Ogni livello dispone di un set di membri, come indicato di seguito:  
  
-   il mondo`= {All}`  
  
-   Continenti`= {North America, Europe}`  
  
-   Paesi`= {Canada, USA, UK, Germany}`  
  
-   Regioni`= {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}`  
  
-   Città`= {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}`  
  
### <a name="members"></a>Members  
 I membri a livello foglia di una gerarchia non hanno elementi figlio e i membri a livello radice non hanno elementi padre. Tutti gli altri membri hanno almeno un elemento padre e almeno un elemento figlio. Ad esempio, un attraversamento parziale dell'albero gerarchico nella dimensione Geography produce le relazioni padre-figlio seguenti:  
  
-   `{All} (parent of) {Europe, North America}`  
  
-   `{North America} (parent of) {Canada, USA}`  
  
-   `{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}`  
  
-   `{USA-NW} (parent of) {Boise, Seattle}`  
  
 I membri possono essere consolidati in una o più gerarchie per dimensione. Si consideri una dimensione temporale in cui sono disponibili due modi per eseguire il rollup a livello di anno dal livello giorni:  
  
 In questo esempio viene illustrata anche un'altra caratteristica: alcuni membri del livello della settimana della gerarchia di anno-settimana non vengono visualizzati in alcun livello della gerarchia Year-Quarter. Pertanto, una gerarchia non deve includere tutti i membri di una dimensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Modello a oggetti ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (multidimensionale) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Programmazione con ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Utilizzo di ADO con ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Utilizzo dei dati multidimensionali](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
