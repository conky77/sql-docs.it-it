---
title: RecordCreateOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65fe33b73cf77a27fcd69743ffb09cb05e197797
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917338"
---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Specifica se deve essere aperto un **record** esistente o se è stato creato un nuovo **record** per il metodo di [apertura](../../../ado/reference/ado-api/open-method-ado-record.md) dell'oggetto [record](../../../ado/reference/ado-api/record-object-ado.md) . I valori possono essere combinati con un operatore AND.  
  
|Costante|valore|Descrizione|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|Crea un nuovo **record** nel nodo specificato dal parametro *source* , anziché aprire un **record**esistente. Se l'origine punta a un nodo esistente, si verifica un errore di run-time, a meno che **adCreateCollection** non sia combinato con **adOpenIfExists** o **adCreateOverwrite**.|  
|**adCreateNonCollection**|0|Crea un nuovo **record** di tipo [adSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adCreateOverwrite**|0x4000000|Modifica i flag di creazione **adCreateCollection**, **adCreateNonCollection**e **adCreateStructDoc**. Quando si usa o con questo valore e uno dei valori del flag di creazione, se l'URL di origine punta a un nodo o a un **record**esistente, il **record** esistente viene sovrascritto e ne viene creato uno nuovo al suo posto. Questo valore non può essere utilizzato insieme a **adOpenIfExists**.|  
|**adCreateStructDoc**|0x80000000|Crea un nuovo **record** di tipo [adStructDoc](../../../ado/reference/ado-api/recordtypeenum.md), anziché aprire un **record**esistente.|  
|**adFailIfNotExists**|-1|Default. Genera un errore di run-time se l' *origine* punta a un nodo inesistente.|  
|**adOpenIfExists**|0x2000000|Modifica i flag di creazione **adCreateCollection**, **adCreateNonCollection**e **adCreateStructDoc**. Quando si usa o con questo valore e uno dei valori del flag di creazione, se l'URL di origine punta a un oggetto **record** o nodo esistente, il provider deve aprire il **record** esistente anziché crearne uno nuovo. Questo valore non può essere utilizzato insieme a **adCreateOverwrite**.|  
  
## <a name="adowfc-equivalent"></a>Equivalente ADO/WFC  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Open (Record - ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
