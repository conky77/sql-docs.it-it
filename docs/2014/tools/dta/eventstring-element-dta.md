---
title: Elemento EventString (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30e46515fda5bf03a96e9f1168b470f635698d07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211111"
---
# <a name="eventstring-element-dta"></a>Elemento EventString (DTA)
  Specifica il carico di lavoro di uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] direttamente nel file di input XML.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Weight`|Facoltativa. Specifica il fattore di ponderazione, o fattore di importanza, della query per l'evento specificato. Per specificare il fattore di ponderazione, utilizzare un tipo di dati `float`. Ad esempio, `Weight`="100.01". Il valore minimo che è possibile specificare per `Weight` è "0".|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|
  `string`, lunghezza illimitata.|  
|**Valore predefinito**|No.|  
|**Occorrenza**|Obbligatorio una sola volta se non viene specificato un altro tipo di carico di lavoro. È necessario specificare un elemento figlio `EventString`, `File` o `Database` per l'elemento padre `Workload`, ma è possibile utilizzare un solo tipo. Se ad esempio si specifica un carico di lavoro con l'elemento `EventString`, non sarà possibile specificare anche un carico di lavoro con l'elemento `File` nello stesso file di input XML.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento workload &#40;DTA&#41;](workload-element-dta.md)|  
|**Elementi figlio**|No.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con carico di lavoro inline &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
