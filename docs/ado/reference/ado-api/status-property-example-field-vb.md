---
title: Esempio di proprietà Status (Field) (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c28a0b615a9f250c8539e87abf9fefbc11f513ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67916824"
---
# <a name="status-property-example-field-vb"></a>Esempio della proprietà Status (Field) (VB)
Nell'esempio seguente viene aperto un documento da una cartella di lettura/scrittura utilizzando il [provider di pubblicazione Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). La proprietà [status](../../../ado/reference/ado-api/status-property-ado-field.md) di un [oggetto campo](../../../ado/reference/ado-api/field-object.md) del [record](../../../ado/reference/ado-api/record-object-ado.md) verrà prima impostata su **adFieldPendingInsert**, quindi verrà aggiornata in **adFieldOK**.  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=https://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 Nell'esempio seguente viene eliminato un **campo** noto da un **record** aperto da un documento. La proprietà **status** verrà prima impostata su **AdFieldOK**, quindi **adFieldPendingUnknown**.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 Il codice seguente elimina un **campo** da un **record** aperto in un documento di sola lettura. **Lo stato** verrà impostato su **adFieldPendingDelete**. Al momento dell' [aggiornamento](../../../ado/reference/ado-api/update-method.md), l'eliminazione avrà esito negativo e **lo stato** sarà **adFieldPendingDelete** più **adFieldPermissionDenied**. [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) cancella l'impostazione **dello stato** in sospeso.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Field (oggetto)](../../../ado/reference/ado-api/field-object.md)   
 [Oggetto record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Proprietà Status (Field - ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)
