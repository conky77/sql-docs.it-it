---
title: Il Provider di persistenza Microsoft OLE DB (ADO Service Provider) | Documenti Microsoft
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
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b3851a5ba05e965114ba0c9f50df1f2cb59d4fd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Cenni preliminari sul Provider di persistenza Microsoft OLE DB
Provider Microsoft OLE DB persistenza consente di salvare un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto in un file e successivamente ripristinare che **Recordset** oggetto dal file. Informazioni sullo schema, i dati e vengono mantenute le modifiche in sospeso.

 È possibile salvare il **Recordset** in formato proprietario di Advanced dati tabella gramma (ADTG) o il formato di Extensible Markup Language (XML) aperto.

## <a name="provider-keyword"></a>Parola chiave del provider
 Per richiamare questo provider, specificare la parola chiave e il valore seguente nella stringa di connessione.

```
"Provider=MSPersist"
```

## <a name="errors"></a>Errori
 I seguenti errori generati da questo provider possono essere rilevati nell'applicazione.

|Costante|Description|
|--------------|-----------------|
|E_BADSTREAM|Il file aperto non dispone di un formato valido (ovvero, il formato non è ADTG o XML).|
|E_CANTPERSISTROWSET|Il **Recordset** oggetto salvato include caratteristiche che ne impediscono l'archiviazione.|

## <a name="remarks"></a>Osservazioni
 Provider Microsoft OLE DB persistenza non espone proprietà dinamiche.

 Attualmente, solo con parametri gerarchici **Recordset** oggetti non possono essere salvati.

 Per ulteriori informazioni sull'archiviazione in modo permanente **Recordset** degli oggetti, vedere [persistenza Recordset](../../../ado/guide/data/more-about-recordset-persistence.md).

 Quando viene utilizzato un flusso per aprire un **Recordset,** non deve esistere alcun parametro specificato è diverso dal *origine* parametro del **aprire** metodo.

## <a name="see-also"></a>Vedere anche
[Provider di persistenza Microsoft OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)