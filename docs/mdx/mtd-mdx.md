---
title: MTD (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e604f66e48c8c8bb93ff5fd4abb174449f0fcdd9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088437"
---
# <a name="mtd-mdx"></a>Mtd (MDX)


  Restituisce un set di membri di pari livello dallo stesso livello di un membro dato, iniziando dal primo membro di pari livello e terminando con il membro dato, in base al vincolo imposto dal livello Anno della dimensione temporale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Se non viene specificata un'espressione di membro, l'impostazione predefinita è il membro corrente della prima gerarchia con un livello di tipo *months* nella prima dimensione di tipo *Time* del gruppo di misure.  
  
 La funzione **MTD** è una funzione di collegamento per la funzione [PeriodsToDate](../mdx/periodstodate-mdx.md) quando la proprietà Type della gerarchia dell'attributo su cui si basa un livello è impostata su *months*. In altre parole, `Mtd(Member_Expression)` equivale a `PeriodsToDate(Month_Level_Expression,Member_Expression)`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la somma dei costi di spedizione nell'ultimo mese per le vendite Internet effettuate fino al 20 luglio 2002.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sum &#40;MDX&#41;](../mdx/sum-mdx.md)   
 [Guida di riferimento alle funzioni MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)  
  
  
