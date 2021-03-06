---
title: Proprietà Source (record ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::Source
- _Record::PutRefSource
- _Record::GetSource
- _Record::put_Source
- _Record::putref_Source
- _Record::get_Source
helpviewer_keywords:
- Source property [ADO Record]
ms.assetid: 2c18279e-6f35-4af0-b12e-8f1543d9ed20
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b1870d8cd8253e1b6de74ce093d51ca6e33c5c6d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67930930"
---
# <a name="source-property-ado-record"></a>Proprietà Source (Record - ADO)
Indica l'origine dati o l'oggetto rappresentato dal [record](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta o restituisce un valore **Variant** che indica l'entità rappresentata dal **record**.  
  
## <a name="remarks"></a>Osservazioni  
 La proprietà **source** restituisce l'argomento di *origine* del metodo di [apertura](../../../ado/reference/ado-api/open-method-ado-record.md) dell'oggetto **record** . Può contenere una stringa URL assoluta o relativa. È possibile utilizzare un URL assoluto senza impostare la proprietà [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) per aprire direttamente l'oggetto **record** . In questo caso viene creato un oggetto **connessione** implicito.  
  
 La proprietà **source** può inoltre contenere un riferimento a un **Recordset**già aperto, che consente di aprire un oggetto **record** che rappresenta la riga corrente nel **Recordset**.  
  
 La proprietà **source** può inoltre contenere un riferimento a un oggetto [Command](../../../ado/reference/ado-api/command-object-ado.md) che restituisce una singola riga di dati dal provider.  
  
 Se viene impostata anche la proprietà **ActiveConnection** , la proprietà **source** deve puntare a un oggetto esistente nell'ambito di tale connessione. Negli spazi dei nomi strutturati ad albero, ad esempio, se la proprietà di **origine** contiene un URL assoluto, deve puntare a un nodo presente all'interno dell'ambito del nodo identificato dall'URL nella stringa di connessione. Se la proprietà di **origine** contiene un URL relativo, viene convalidata nel contesto impostato dalla proprietà **ActiveConnection** .  
  
 La proprietà di **origine** è di lettura/scrittura mentre l'oggetto **record** è chiuso ed è di sola lettura mentre l'oggetto **record** è aperto.  
  
> [!NOTE]
>  Gli URL che usano lo schema http richiameranno automaticamente il [provider di Microsoft OLE DB per la pubblicazione Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluto e relativo](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Source (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)   
 [Proprietà Source (Recordset - ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)
