---
title: Elemento Server (DTA)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 23609b4054b456eed8c95659a3984d3f2f03aec3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "75307871"
---
# <a name="server-element-dta"></a>Elemento Server (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Contiene le informazioni di identificazione del server sul quale risiede il database che si desidera ottimizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|No.|  
|**Valore predefinito**|No.|  
|**Occorrenza**|Obbligatorio una sola volta per ogni elemento **DTAInput** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DTAInput &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**Elementi figlio**|[Elemento Name per Server &#40;DTA&#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Elemento Database per Server &#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>Osservazioni  
 È possibile specificare solo un elemento **Server** per l'elemento **DTAInput** . Questo elemento appartiene al nome **ServerDetailsTypecomplexType** nell'XML Schema di DTA. Non confondere l'elemento **Server** con l'elemento figlio dell'elemento **Configuration** . Per altre informazioni, vedere [Elemento Server per Configuration &#40;DTA&#41;](../../tools/dta/server-element-for-configuration-dta.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come specificare la tabella **Sales.SalesPerson** nel database **AdventureWorks** in SERVER001:  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
