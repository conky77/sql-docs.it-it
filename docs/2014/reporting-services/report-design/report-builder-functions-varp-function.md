---
title: Funzione VarP (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e4f86ab3-bdb3-4e4a-9a9d-7ae7abdf4dc4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b143f6e5b411a6e3f04509b2dc88459a92002428
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105113"
---
# <a name="varp-function-report-builder-and-ssrs"></a>Funzione VarP (Generatore report e SSRS)
  Viene restituita la varianza della popolazione di tutti i valori numerici non Null specificati dall'espressione, valutata nel contesto dell'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
VarP(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Parametri  
 *expression*  
 (`Integer` o `Float`) Espressione su cui eseguire l'aggregazione.  
  
 *ambito*  
 (`String`) Facoltativo. Nome di un set di dati, gruppo o area dati che contiene gli elementi del report a cui applicare la funzione di aggregazione. Se si omette *scope* , viene usato l'ambito corrente.  
  
 *ricorsivi*  
 (**Enumerated Type**) Facoltativo. 
  `Simple` (valore predefinito) o `RdlRecursive`. Specifica se eseguire l'aggregazione in modo ricorsivo.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un valore `Decimal` per le espressioni decimali e un valore `Double` per tutte le altre espressioni.  
  
## <a name="remarks"></a>Osservazioni  
 Il set di dati specificato nell'espressione deve essere dello stesso tipo di dati. Per convertire dati con più tipi di dati numerici nello stesso tipo di dati, usare funzioni di conversione come `CInt`, `CDbl` o `CDec`. Per altre informazioni, vedere [Funzioni di conversione del tipo](https://go.microsoft.com/fwlink/?LinkId=96142).  
  
 Il valore di *scope* deve essere una costante di tipo stringa e non può essere un'espressione. Per aggregazioni o aggregazioni esterne che non specificano altre aggregazioni, *scope* deve fare riferimento all'ambito corrente o a un ambito contenitore. Per le aggregazioni di aggregazioni, le aggregazioni nidificate possono specificare un ambito figlio.  
  
 *Expression* può contenere chiamate alle funzioni di aggregazione nidificate con le eccezioni e le condizioni seguenti:  
  
-   *Scope* per le aggregazioni nidificate deve corrispondere o essere contenuto nell'ambito dell'aggregazione esterna. Per tutti gli ambiti distinti nell'espressione, un ambito deve essere in una relazione figlio con tutti gli altri ambiti.  
  
-   *Scope* per le aggregazioni nidificate non può essere il nome di un set di dati.  
  
-   L' *espressione* non deve `First`contenere `Last`funzioni `Previous`,, `RunningValue` o.  
  
-   *Expression* non deve contenere aggregazioni nidificate che specificano *recursive*.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Per altre informazioni sulle aggregazioni ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene specificata una varianza della popolazione dei totali degli elementi nel gruppo o nell'area dati `Order` .  
  
```  
=VarP(Fields!LineTotal.Value, "Order")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
