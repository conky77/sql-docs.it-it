---
title: Metodo getBinaryStream (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBinaryStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de22a6c4-1ba3-4ed0-91a2-bf235c2ceec3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0add171861f2ea9e021b9f9342968baf1601557
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "67953705"
---
# <a name="getbinarystream-method-int"></a>Metodo getBinaryStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore dell'indice della colonna designata nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come flusso binario di byte non interpretati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.InputStream getBinaryStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Valore **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto InputStream.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getBinaryStream viene specificato dal metodo getBinaryStream nell'interfaccia java.sql.ResultSet.  
  
 Questo metodo può essere usato solo con i tipi di dati binary, varbinary, varbinary(max) e image di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se si tenta di utilizzarlo con altri tipi di dati genererà un'eccezione.  
  
 Una volta ottenuto il valore come flusso tramite questo metodo, tale valore può essere letto in blocchi dal flusso. Questo metodo è particolarmente adatto per il recupero di valori LONGVARBINARY di grandi dimensioni.  
  
> [!NOTE]  
>  Prima di ottenere il valore di qualsiasi altra colonna, è necessario leggere tutti i dati nel flusso restituito. La chiamata successiva a un metodo di richiamo chiude in modo implicito il flusso. Un flusso può anche restituire 0 quando viene chiamato il metodo InputStream.available, siano o meno disponibili dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
