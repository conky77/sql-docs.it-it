---
title: Funzione Max (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- max function [XQuery]
- fn:max function
ms.assetid: 5ee625c0-044a-4cda-b210-02b64e619d65
author: rothja
ms.author: jroth
ms.openlocfilehash: e47539a350a2918ef24c47e3c1eca270d4aeb72e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985956"
---
# <a name="aggregate-functions---max"></a>Funzioni di aggregazione - max
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce da una sequenza di valori atomici, *$arg*, un elemento il cui valore è maggiore di quello di tutti gli altri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:max($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Argomenti  
 *$arg*  
 Sequenza di valori atomici dalla quale deve essere restituito il valore massimo.  
  
## <a name="remarks"></a>Osservazioni  
 Tutti i tipi di valori atomizzati passati a **Max ()** devono essere sottotipi dello stesso tipo di base. I tipi di base accettati sono i tipi che supportano l'operazione **gt** . Tra questi tipi sono inclusi i tre tipi di base numerici predefiniti, ovvero i tipi di base di data/ora xs:string, xs:boolean e xdt:untypedAtomic. Per i valori di tipo xdt:untypedAtomic viene eseguito il cast a xs:double. Se è presente una combinazione di questi tipi o se vengono passati altri valori di altri tipi, viene generato un errore statico.  
  
 Il risultato di **Max ()** riceve il tipo di base dei tipi passati, ad esempio xs: Double nel caso di xdt: untypedAtomic. Se l'input è una sequenza vuota calcolata in modo statico, la sequenza vuota è implicita e viene restituito un errore statico.  
  
 La funzione **Max ()** restituisce un valore nella sequenza maggiore di qualsiasi altro oggetto nella sequenza di input. Per i valori xs:string, vengono utilizzate le regole di confronto predefinite dei punti di codice Unicode. Se non è possibile eseguire il cast di un valore xdt: untypedAtomic a xs: Double, il valore viene ignorato nella sequenza di input *$arg*. Se l'input è una sequenza vuota calcolata in modo dinamico, viene restituita la sequenza vuota.  
  
## <a name="examples"></a>Esempi  
 In questo argomento vengono forniti esempi di XQuery sulle istanze XML archiviate **** in diverse colonne di tipo [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] XML nel database.  
  
### <a name="a-using-the-max-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-that-have-the-most-labor-hours"></a>R. Utilizzo della funzione XQuery max() per trovare i centri di lavorazione del processo di produzione che hanno il maggior numero di ore di manodopera  
 La query fornita in [funzione min (XQuery)](../xquery/aggregate-functions-min.md) può essere riscritta in modo da utilizzare la funzione **Max ()** .  
  
## <a name="implementation-limitations"></a>Limitazioni di implementazione  
 Limitazioni:  
  
-   La funzione **Max (**) esegue il mapping di tutti i numeri interi a xs: Decimal.  
  
-   La funzione **Max ()** su valori di tipo xs: Duration non è supportata.  
  
-   Non sono supportate le sequenze con combinazioni di tipi che non rispettano i limiti del tipo di base.  
  
-   Non è supportata l'opzione sintattica che fornisce le regole di confronto.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
