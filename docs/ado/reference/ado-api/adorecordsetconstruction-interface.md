---
title: Interfaccia ADORecordsetConstruction | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1e1d14255acd4cc7f18abea1c494353ef970903c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920799"
---
# <a name="adorecordsetconstruction-interface"></a>Interfaccia ADORecordsetConstruction
L'interfaccia **ADORecordsetConstruction** viene utilizzata per costruire un oggetto **Recordset** ADO da un oggetto OLE DB **set di righe** in un'applicazione C/C++.  
  
 Questa interfaccia supporta le proprietà seguenti:  
  
## <a name="properties"></a>Proprietà  
  
|||  
|-|-|  
|[Capitolo](../../../ado/reference/ado-api/chapter-property-ado.md)|Lettura/Scrittura.<br />Ottiene o imposta un oggetto OLE DB **capitolo** da/in questo oggetto **Recordset** ADO.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Lettura/Scrittura.<br />Ottiene o imposta un OLE DB oggetto **RowPosition** da/in questo oggetto **Recordset** ADO.|  
|[Set di righe](../../../ado/reference/ado-api/rowset-property-ado.md)|Lettura/Scrittura.<br />Ottiene o imposta un oggetto OLE DB **set di righe** da/in questo oggetto **Recordset** ADO.|  
  
## <a name="methods"></a>Metodi  
 No.  
  
## <a name="events"></a>Eventi  
 No.  
  
## <a name="remarks"></a>Osservazioni  
 Dato un oggetto **OLE DB set** di`pRowset`righe (), la costruzione di un oggetto **Recordset** ADO (`adoRs`) equivale alle tre operazioni di base seguenti:  
  
1.  Creazione di un oggetto **Recordset** ADO:  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  Eseguire una query sull'interfaccia **IADORecordsetConstruction** sull'oggetto **Recordset** :  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  Chiamare il `IADORecordsetConstruction::put_Rowset` Metodo Property per impostare l'oggetto `Rowset` OLE DB sull'oggetto ADO `Recordset` :  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 L' `adoRs` oggetto risultante rappresenta ora l'oggetto **Recordset** ADO costruito dall'oggetto set di **righe** OLE DB.  
  
 È anche possibile costruire un oggetto **Recordset** ADO da un OLE DB un **capitolo** o un oggetto **RowPosition** .  
  
## <a name="requirements"></a>Requisiti  
 **Versione:** ADO 2,0 e versioni successive  
  
 **Libreria:** msado15. dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Proprietà Rowset (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
