---
title: Metodo getObjectInstance (SQLServerDataSourceObjectFactory) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSourceObjectFactory.getObjectInstance
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0a1503e2-e991-4d70-a223-087fc63baf73
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de25e608c9fbdbdf6ff91d08e7a6502765bb590e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981057"
---
# <a name="getobjectinstance-method-sqlserverdatasourceobjectfactory"></a>Metodo getObjectInstance (SQLServerDataSourceObjectFactory)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un'istanza dell'oggetto origine dati specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.Object getObjectInstance(java.lang.Object ref,  
                                          javax.naming.Name name,  
                                          javax.naming.Context c,  
                                          java.util.Hashtable h)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ref*  
  
 Valore **Object**.  
  
 *nome*  
  
 Nome dell'oggetto .  
  
 *c*  
  
 Contesto relativo al nome specificato.  
  
 *h*  
  
 Ambiente utilizzato nella creazione dell'oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Valore **Object**.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getObjectInstance viene specificato dal metodo getObjectInstance nell'interfaccia javax.naming.spi.ObjectFactory.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-methods.md)   
 [Membri di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Classe SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)  
  
  
