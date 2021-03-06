---
title: Funzioni di aggregazione, funzione CALC e parola chiave NEW | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], functions
- CALC function [ADO]
- NEW keyword [ADO]
- aggregate functions [ADO]
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a7ed836b9b57ddd690dd85dd94cc12cb967c472
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926003"
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>Funzioni di aggregazione, funzione CALC e parola chiave NEW
Data Shaping supporta le funzioni seguenti. Il nome assegnato al capitolo contenente la colonna da operare è l' *alias del capitolo*.  
  
 Un alias del capitolo può essere completo, costituito da ogni nome di colonna del capitolo che conduce al capitolo contenente il *nome della colonna,* tutti separati da punti. Se, ad esempio, il capitolo padre, chap1, contiene un capitolo figlio CHAP2 con una colonna Amount, AMT, il nome completo sarà chap1. CHAP2. AMT.  
  
|Funzioni di aggregazione|Descrizione|  
|-------------------------|-----------------|  
|SUM (*Chapter-alias*.* Nome colonna*)|Calcola la somma di tutti i valori nella colonna specificata.|  
|AVG (*Chapter-alias*.* Nome colonna*)|Calcola la media di tutti i valori nella colonna specificata.|  
|MAX (*alias di capitolo*.* Nome colonna*)|Calcola il valore massimo nella colonna specificata.|  
|MIN (*Chapter-alias*.* Nome colonna*)|Calcola il valore minimo nella colonna specificata.|  
|COUNT (*alias capitolo*[.* Nome colonna*])|Conta il numero di righe nell'alias specificato. Se viene specificata una colonna, nel conteggio vengono incluse solo le righe per le quali la colonna è non null.|  
|STDEV (*Chapter-alias*.* Nome colonna*)|Calcola la deviazione standard nella colonna specificata.|  
|ANY (*alias del capitolo*.* Nome colonna*)|Valore della colonna specificata. ANY presenta un valore stimabile solo quando il valore della colonna è lo stesso per tutte le righe del capitolo.<br /><br /> **Nota** Se la colonna non contiene lo stesso valore per tutte le righe nel capitolo, il comando SHAPE restituisce arbitrariamente uno dei valori in modo che corrisponda al valore della funzione ANY.|  
  
|Espressione calcolata|Descrizione|  
|---------------------------|-----------------|  
|CALCOLO (*espressione*)|Calcola un'espressione arbitraria, ma solo sulla riga del **Recordset** che contiene la funzione Calc. È consentita qualsiasi espressione che utilizza queste [funzioni Visual Basic, Applications Edition (VBA)](../../../ado/guide/data/visual-basic-for-applications-functions.md) .|  
  
|NUOVA parola chiave|Descrizione|  
|-----------------|-----------------|  
|NUOVO *tipo di campo* [(*width* &#124; *scale* &#124; *Precision* &#124; *Error* [, *scale* &#124; *Error*])]|Aggiunge al **Recordset**una colonna vuota del tipo specificato.|  
  
 Il *tipo di campo* passato con la parola chiave New può essere uno dei tipi di dati seguenti.  
  
|Tipi di dati OLE DB|Tipi di dati ADO equivalenti|  
|-----------------------|-----------------------------------|  
|DBTYPE_BSTR|adBSTR|  
|DBTYPE_BOOL|adBoolean|  
|DBTYPE_DECIMAL|adDecimal|  
|DBTYPE_UI1|adUnsignedTinyInt|  
|DBTYPE_I1|adTinyInt|  
|DBTYPE_UI2|adUnsignedSmallInt|  
|DBTYPE_UI4|adUnsignedInt|  
|DBTYPE_I8|adBigInt|  
|DBTYPE_UI8|adUnsignedBigInt|  
|DBTYPE_GUID|adGuid|  
|DBTYPE_BYTES|adBinary, AdVarBinary, adLongVarBinary|  
|DBTYPE_STR|adChar, adVarChar, adLongVarChar|  
|DBTYPE_WSTR|adWChar, adVarWChar, adLongVarWChar|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 Quando il nuovo campo è di tipo Decimal (in OLE DB, DBTYPE_DECIMAL o in ADO, adDecimal), è necessario specificare i valori di precisione e scala.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di data shaping](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica forma formale](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
