---
title: Esempio del metodo Refresh (VB) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Refresh method [ADO], Visual Basic example
ms.assetid: f5375fa1-4711-4f7e-9ba4-54c427f71325
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2dffab0ab4a42a3a67258a6ba6af44124857e593
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="refresh-method-example-vb"></a>Esempio del metodo Refresh (VB)
In questo esempio viene illustrato l'utilizzo di [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) per aggiornare il [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme per una stored procedure [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto.  
  
```  
'BeginRefreshVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection strings  
  
    ' connection and recordset variables  
    Dim Cnxn As ADODB.Connection  
    Dim cmdByRoyalty As ADODB.Command  
    Dim rstByRoyalty As ADODB.Recordset  
    Dim rstAuthors As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
     ' record variables  
    Dim intRoyalty As Integer  
    Dim strAuthorID As String  
    Dim strRoyalty As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open a command object for a stored procedure  
    ' with one parameter  
    Set cmdByRoyalty = New ADODB.Command  
    Set cmdByRoyalty.ActiveConnection = Cnxn  
    cmdByRoyalty.CommandText = "byroyalty"  
    cmdByRoyalty.CommandType = adCmdStoredProc  
    cmdByRoyalty.Parameters.Refresh  
  
    ' Get paramater value, execute the command  
    ' and store the results in a recordset  
    strRoyalty = InputBox("Enter royalty:")  
    If strRoyalty = "" Then  
        Err.Raise 1, , "You either didn't enter royalty or canceled the input box. Exit the application"  
    End If  
  
    intRoyalty = Trim(strRoyalty)  
    cmdByRoyalty.Parameters(1) = intRoyalty  
    Set rstByRoyalty = cmdByRoyalty.Execute()  
  
    ' Open the Authors table to get author names for display  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenForwardOnly, adLockPessimistic, adCmdTable  
  
    ' Print current data in the recordset  
    ' and add author names  
    Debug.Print "Authors with " & intRoyalty & " percent royalty"  
  
    Do Until rstByRoyalty.EOF  
        strAuthorID = rstByRoyalty!au_id  
        Debug.Print "   " & rstByRoyalty!au_id & ", ";  
        rstAuthors.Filter = "au_id = '" & strAuthorID & "'"  
        Debug.Print rstAuthors!au_fname & " "; rstAuthors!au_lname  
        rstByRoyalty.MoveNext  
    Loop  
  
    ' clean up  
    rstByRoyalty.Close  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstByRoyalty = Nothing  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstByRoyalty Is Nothing Then  
        If rstByRoyalty.State = adStateOpen Then rstByRoyalty.Close  
    End If  
    Set rstByRoyalty = Nothing  
  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndRefreshVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Metodo Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)