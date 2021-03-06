---
title: Proprietà SortColumn (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b5a9c3f9f50968f3b5e8085052917397bcd90226
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963402"
---
# <a name="sortcolumn-property-rds"></a>Proprietà SortColumn (Servizi Desktop remoto)
Indica in quale colonna ordinare i record.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Parametri  
 *DataControl*  
 Variabile oggetto che rappresenta un Servizi Desktop remoto [. Oggetto DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *Stringa*  
 Valore **stringa** che rappresenta il nome o l'alias della colonna in base alla quale ordinare i record.  
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà **SortColumn**, [SortDirection](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md)e [FilterColumn offrono](../../../ado/reference/rds-api/filtercolumn-property-rds.md) forniscono funzionalità di ordinamento e filtro nella cache sul lato client. La funzionalità di ordinamento ordina i record in base ai valori di una colonna. La funzionalità di filtro Visualizza un subset di record in base ai criteri di ricerca, mentre il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) completo viene mantenuto nella cache. Il metodo [Reset](../../../ado/reference/rds-api/reset-method-rds.md) eseguirà i criteri e sostituirà il **Recordset** corrente con un **Recordset**aggiornabile.  
  
 Per eseguire l'ordinamento in un **Recordset**, è innanzitutto necessario salvare le modifiche in sospeso. Se si utilizza **RDS. DataControl**, è possibile usare il metodo [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) . Ad esempio, se il Servizi Desktop remoto **. DataControl** è denominato ADC1, il codice è `ADC1.SubmitChanges`. Se si utilizza un **Recordset**ADO, è possibile utilizzare il relativo metodo [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) . L'uso di **UpdateBatch** è il metodo consigliato per gli oggetti **Recordset** creati con il metodo [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) . Ad esempio, il codice potrebbe essere `myRS.UpdateBatch` o `ADC1.Recordset.UpdateBatch`.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà FilterColumn offrono, FilterCriterion, FilterValue, SortColumn e SortDirection e metodo Reset (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort (proprietà)](../../../ado/reference/ado-api/sort-property.md)   
 [Proprietà SortDirection (Servizi Desktop remoto)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





