---
title: Metodo Reset (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reset method [ADO]
ms.assetid: 3957197a-f543-4d6b-9e11-67a77c2063b7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 416aaefa95871e909a12117756ea59747c555650
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963499"
---
# <a name="reset-method-rds"></a>Metodo Reset (Servizi Desktop remoto)
Esegue l'ordinamento o il filtro su un **Recordset** lato client in base alle proprietà di ordinamento e filtro specificate.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Variabile oggetto che rappresenta un Servizi Desktop remoto [. Oggetto DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *valore*  
 Facoltativa. Valore **booleano** che è **true** (impostazione predefinita) se si desidera filtrare il set di righe "filtrato" corrente. **False** indica che si filtra il set di righe originale, rimuovendo eventuali opzioni di filtro precedenti.  
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)e [FilterColumn offrono](../../../ado/reference/rds-api/filtercolumn-property-rds.md) forniscono funzionalità di ordinamento e filtro nella cache sul lato client. La funzionalità di ordinamento ordina i record in base ai valori di una colonna. La funzionalità di filtro Visualizza un subset di record in base a un criterio di ricerca, mentre il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) completo viene mantenuto nella cache. Il metodo **Reset** eseguirà i criteri e sostituirà il **Recordset** corrente con un **Recordset**aggiornabile.  
  
 Se sono state apportate modifiche ai dati originali che non sono stati inviati, il metodo **Reset** avrà esito negativo. Per prima cosa, utilizzare il metodo [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) per salvare le modifiche in un **Recordset**di lettura/scrittura, quindi utilizzare il metodo **Reset** per ordinare o filtrare i record.  
  
 Se si desidera eseguire più di un filtro sul set di righe, è possibile utilizzare l'argomento *booleano* facoltativo con il metodo **Reset** . L'esempio seguente illustra come farlo:  
  
```  
ADC.SQL = "Select au_lname from authors"  
ADC.Refresh    ' Get the new rowset.  
  
ADC.FilterColumn = "au_lname"  
ADC.FilterCriterion = "<"  
ADC.FilterValue = "'M'"  
ADC.Reset         ' Rowset now has all Last Names < "M".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'F'"  
' Passing True is not necessary, because it is the   
' default filter on the current "filtered" rowset.  
ADC.Reset(TRUE)     ' Rowset now has all Last   
                    ' Names < "M" and > "F".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'T'"  
' Filter on the original rowset, throwing out the  
' previous filter options.  
ADC.Reset(FALSE)   ' Rowset now has all Last Names > "T".  
```  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà FilterColumn offrono, FilterCriterion, FilterValue, SortColumn e SortDirection e metodo Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Metodo SubmitChanges (Servizi Desktop remoto)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



