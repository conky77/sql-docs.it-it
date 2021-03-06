---
title: Metodo isReadOnly (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isReadOnly
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 902fd2c1-05e0-436e-9779-c048cdb8475a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 708060b6192e47a126c9c4c3ea47052c098bb1fd
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977327"
---
# <a name="isreadonly-method-sqlserverconnection"></a>Metodo isReadOnly (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) è in modalità di sola lettura.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato da [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isReadOnly()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la connessione è in modalità di sola lettura. **false** in caso contrario.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isReadOnly viene specificato dal metodo isReadOnly nell'interfaccia java.sql.Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
