---
title: Interfaccia ISQLServerPreparedStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cf87892e-5c34-4ac6-8258-c2a81e117b26
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 05fda4ea42c1819f3cbb4f16fcc7f02da2a06b8e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977430"
---
# <a name="isqlserverpreparedstatement-interface"></a>Interfaccia ISQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta l'implementazione di base della funzionalità dell'istruzione preparata di JDBC. Questa interfaccia è stata aggiunta in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.sql.PreparedStatement, [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public interface ISQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Osservazioni  
 Questa interfaccia viene implementata dalla [classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
 L'interfaccia espone i metodi specifici di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] seguenti:  
  
|Metodo|Per ulteriori informazioni, vedere|  
|------------|-------------------------------|  
|public void setDateTimeOffset(int, microsoft.sql.DateTimeOffset)|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sull'API del driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
