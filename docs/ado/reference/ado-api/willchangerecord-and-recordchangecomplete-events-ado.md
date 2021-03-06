---
title: Eventi WillChangeRecord e RecordChangeComplete (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- RecordChangeComplete
- Recordset::WillChangeRecord
- WillChangeRecord
- Recordset::RecordChangeComplete
helpviewer_keywords:
- WillChangeRecord event [ADO]
- recordchangecomplete event [ADO]
ms.assetid: cbc369fd-63af-4a7d-96ae-efa91b78ca69
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e632db34fbbacbee61cd943067052af27a8cfe8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938670"
---
# <a name="willchangerecord-and-recordchangecomplete-events-ado"></a>Eventi WillChangeRecord e RecordChangeComplete (ADO)
L'evento **WillChangeRecord** viene chiamato prima della modifica di uno o più record (righe) nel [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) . L'evento **RecordChangeComplete** viene chiamato dopo la modifica di uno o più record.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
WillChangeRecord adReason, cRecords, adStatus, pRecordset  
RecordChangeCompleteadReason, cRecords, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *adReason*  
 Valore [EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md) che specifica il motivo di questo evento. Il valore può essere **adRsnAddNew**, **adRsnDelete**, **adRsnUpdate**, **adRsnUndoUpdate**, **adRsnUndoAddNew**, **adRsnUndoDelete**o **adRsnFirstChange**.  
  
 *cRecords*  
 Valore **Long** che indica il numero di record modificati (interessati).  
  
 *pError*  
 Oggetto [Error](../../../ado/reference/ado-api/error-object.md) . Viene descritto l'errore che si è verificato se il valore di *adStatus* è **adStatusErrorsOccurred**; in caso contrario, non è impostato.  
  
 *adStatus*  
 Valore di stato di [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) .  
  
 Quando viene chiamato **WillChangeRecord** , questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento è riuscita. Viene impostato su **adStatusCantDeny** se questo evento non può richiedere l'annullamento dell'operazione in sospeso.  
  
 Quando viene chiamato **RecordChangeComplete** , questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento è stata eseguita correttamente oppure su **adStatusErrorsOccurred** se l'operazione non è riuscita.  
  
 Prima della restituzione di **WillChangeRecord** , impostare questo parametro su **adStatusCancel** per richiedere l'annullamento dell'operazione che ha causato questo evento o impostare questo parametro su **adStatusUnwantedEvent** per impedire le notifiche successive.  
  
 Prima della restituzione di **RecordChangeComplete** , impostare questo parametro su **adStatusUnwantedEvent** per impedire le notifiche successive.  
  
 *pRecordset*  
 Oggetto **Recordset** . **Recordset** per il quale si è verificato l'evento.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile che si verifichi un evento **WillChangeRecord** o **RecordChangeComplete** per il primo campo modificato in una riga a causa delle operazioni **Recordset** seguenti: [Update](../../../ado/reference/ado-api/update-method.md), [Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md), [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)e [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md). Il valore del **Recordset** [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) determina quali operazioni provocano l'esecuzione degli eventi.  
  
 Durante l'evento **WillChangeRecord** , la proprietà del [filtro](../../../ado/reference/ado-api/filter-property.md) **Recordset** è impostata su **adFilterAffectedRecords**. Non è possibile modificare questa proprietà durante l'elaborazione dell'evento.  
  
 È necessario impostare il parametro **adStatus** su **adStatusUnwantedEvent** per ogni possibile valore **adReason** per arrestare completamente la notifica degli eventi per qualsiasi evento che includa un parametro **adReason** .  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
