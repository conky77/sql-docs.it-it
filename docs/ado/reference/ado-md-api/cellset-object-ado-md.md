---
title: Oggetto cellt (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9524e9801f284d3dff3125b850cdd1fd32a361a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928641"
---
# <a name="cellset-object-ado-md"></a>Oggetto Cellset (ADO MD)
Rappresenta i risultati di una query multidimensionale. Si tratta di una raccolta di celle selezionate da cubi o altri celle.  
  
## <a name="remarks"></a>Osservazioni  
 I dati all'interno di un insieme di **celle** vengono recuperati mediante l'accesso diretto a un tipo di matrice. È possibile eseguire il drill-down di un membro specifico per ottenere i dati relativi a tale membro. Il codice seguente, ad esempio, restituisce la didascalia del primo membro nella prima posizione sul primo asse di un celle denominato `cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Osservazioni  
 Non esiste alcuna nozione di una cella corrente all'interno di un celle. Al contrario, la proprietà [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) recupera un oggetto [cella](../../../ado/reference/ado-md-api/cell-object-ado-md.md) specifico dal cellt. Gli argomenti della proprietà **Item** determinano quale cella viene recuperata. È possibile specificare il valore ordinale univoco di una cella. È anche possibile recuperare le celle usando i numeri di posizione lungo ogni asse del celle. Per ulteriori informazioni sul recupero di celle, vedere la proprietà [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) .  
  
 Con le raccolte, i metodi e le proprietà di un oggetto di un insieme di **celle** , è possibile eseguire le operazioni seguenti:  
  
-   Associare una connessione aperta a un oggetto set di **celle** impostando la relativa proprietà [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) .  
  
-   Eseguire e recuperare i risultati di una query multidimensionale con il metodo [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) .  
  
-   Recuperare una **cella** da un insieme di **celle** con la proprietà [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) .  
  
-   Restituisce gli oggetti [asse](../../../ado/reference/ado-md-api/axis-object-ado-md.md) che definiscono il gruppo di **celle** con la raccolta [assi](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) .  
  
-   Recuperare le informazioni sulle dimensioni utilizzate per filtrare i dati nel **celle** con la proprietà [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) .  
  
-   Restituisce o specifica la query utilizzata per definire il **celle** con la proprietà di [origine](../../../ado/reference/ado-md-api/source-property-ado-md.md) .  
  
-   Restituisce lo stato corrente del **cellt** (aperto, chiuso, in esecuzione o in connessione) con la proprietà [state](../../../ado/reference/ado-md-api/state-property-ado-md.md) .  
  
-   Chiude un insieme di **celle** aperto con il metodo [Close](../../../ado/reference/ado-md-api/close-method-ado-md.md) .  
  
-   Recuperare le informazioni specifiche del provider relative al **celle** con la raccolta delle [Proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) ADO standard.  
  
 Questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di celle (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Raccolta assi (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Oggetto Cell (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Raccolta Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
