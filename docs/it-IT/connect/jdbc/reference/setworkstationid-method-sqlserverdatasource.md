---
title: Metodo setWorkstationID (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.setWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6e505445d3ea1a7f9ba96b46b2764893d4628ed3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setworkstationid-method-sqlserverdatasource"></a>Metodo setWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome del computer client utilizzato per la connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>Parametri  
 *oggetto workstationID*  
  
 Oggetto **stringa** che contiene il nome del computer client.  
  
## <a name="remarks"></a>Osservazioni  
 L'oggetto workstationID è il nome del computer o della workstation client. Se la proprietà workstationID non è impostata, il valore predefinito viene costruito chiamando il metodo InetAddress.getLocalHost().getHostName(). Se getHostName restituisce un valore vuoto, viene chiamato il metodo getHostAddress().toString().  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  