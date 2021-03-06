---
title: Proprietà SortDirection (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortDirection property [RDS]
ms.assetid: 1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 28f0e247c29673fe4dfec507794ad8977b51fcc1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963411"
---
# <a name="sortdirection-property-rds"></a>Proprietà SortDirection (Servizi Desktop remoto)
Indica se un ordinamento è crescente o decrescente.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Variabile oggetto che rappresenta un Servizi Desktop remoto [. Oggetto DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *Valore*  
 Valore **booleano** che, se impostato su **true**, indica che la direzione di ordinamento è crescente. **False** indica l'ordine decrescente.  
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), **SortDirection**, [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)e [FilterColumn offrono](../../../ado/reference/rds-api/filtercolumn-property-rds.md) forniscono funzionalità di ordinamento e filtro nella cache sul lato client. La funzionalità di ordinamento consente di ordinare i record utilizzando i valori di una colonna. La funzionalità di filtro Visualizza un subset di record in base ai criteri di ricerca, mentre il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) completo viene mantenuto nella cache. Il metodo [Reset](../../../ado/reference/rds-api/reset-method-rds.md) eseguirà i criteri e sostituirà il **Recordset** corrente con un **Recordset**aggiornabile.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà FilterColumn offrono, FilterCriterion, FilterValue, SortColumn e SortDirection e metodo Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort (proprietà)](../../../ado/reference/ado-api/sort-property.md)   
 [Proprietà SortColumn (Servizi Desktop remoto)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)


