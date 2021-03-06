---
title: FieldAttributeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldAttributeEnum
helpviewer_keywords:
- FieldAttributeEnum enumeration [ADO]
ms.assetid: 6e34d886-005a-40dc-bd5c-6adcbf81e5cd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0d375ed3dd4ea7ae7e2e5405d1feec962c5f56ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918699"
---
# <a name="fieldattributeenum"></a>FieldAttributeEnum
Specifica uno o più attributi di un oggetto [campo](../../../ado/reference/ado-api/field-object.md) .  
  
|Costante|valore|Descrizione|  
|--------------|-----------|-----------------|  
|**adFldCacheDeferred**|0x1000|Indica che il provider memorizza nella cache i valori dei campi e che le letture successive vengono eseguite dalla cache.|  
|**adFldFixed**|0x10|Indica che il campo contiene dati a lunghezza fissa.|  
|**adFldIsChapter**|0x2000|Indica che il campo contiene un valore di capitolo, che specifica un recordset figlio specifico correlato a questo campo padre. In genere i campi del capitolo vengono usati con la data shaping o i filtri.|  
|**adFldIsCollection**|0x40000|Indica che il campo specifica che la risorsa rappresentata dal record è una raccolta di altre risorse, ad esempio una cartella, anziché una risorsa semplice, ad esempio un file di testo.|  
|**adFldKeyColumn**|0x8000|Indica che il campo specifica tutta o parte della chiave primaria della colonna.|  
|**adFldIsDefaultStream**|0x20000|Indica che il campo contiene il flusso predefinito per la risorsa rappresentata dal record. Il flusso predefinito, ad esempio, può essere il contenuto HTML di una cartella radice in un sito Web, che viene automaticamente servito quando viene specificato l'URL radice.|  
|**adFldIsNullable**|0x20|Indica che il campo accetta valori null.|  
|**adFldIsRowURL**|0x10000|Indica che il campo contiene l'URL che denomina la risorsa dall'archivio dati rappresentato dal record.|  
|**adFldLong**|0x80|Indica che il campo è un campo binario lungo. Indica inoltre che è possibile usare i metodi [AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md) e [GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md) .|  
|**adFldMayBeNull**|0x40|Indica che è possibile leggere i valori null dal campo.|  
|**adFldMayDefer**|0x2|Indica che il campo è rinviato, ovvero che i valori dei campi non vengono recuperati dall'origine dati con l'intero record, ma solo quando vengono accessibili in modo esplicito.|  
|**adFldNegativeScale**|0x4000|Indica che il campo rappresenta un valore numerico da una colonna che supporta valori di scala negativi. La scala viene specificata dalla proprietà [NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md) .|  
|**adFldRowID**|0x100|Indica che il campo contiene un identificatore di riga persistente in cui non è possibile scrivere e che non dispone di un valore significativo tranne che per identificare la riga, ad esempio un numero di record, un identificatore univoco e così via.|  
|**adFldRowVersion**|0x200|Indica che il campo contiene un tipo di indicatore di data e ora utilizzato per tenere traccia degli aggiornamenti.|  
|**adFldUnknownUpdatable**|0x8|Indica che il provider non è in grado di determinare se è possibile scrivere nel campo.|  
|**adFldUnspecified**|-1 0xFFFFFFFF|Indica che il provider non specifica gli attributi di campo.|  
|**adFldUpdatable**|0x4|Indica che è possibile scrivere nel campo.|  
  
## <a name="adowfc-equivalent"></a>Equivalente ADO/WFC  
 Pacchetto: **com. ms. wfc. Data**  
  
|Costante|  
|--------------|  
|AdoEnums. FieldAttribute. CACHEDEFERRED|  
|AdoEnums. FieldAttribute. FIXED|  
|AdoEnums. FieldAttribute. IsNullable|  
|AdoEnums. FieldAttribute. LONG|  
|AdoEnums. FieldAttribute. MAYBENULL|  
|AdoEnums. FieldAttribute. MAYDEFER|  
|AdoEnums. FieldAttribute. NEGATIVESCALE|  
|AdoEnums. FieldAttribute. ROWID|  
|AdoEnums. FieldAttribute. ROWVERSION|  
|AdoEnums. FieldAttribute. UNKNOWNUPDATABLE|  
|AdoEnums. FieldAttribute. Unspecified|  
|AdoEnums. FieldAttribute. AGGIORNAbile|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Proprietà Attributes (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)|
