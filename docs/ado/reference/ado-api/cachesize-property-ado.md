---
title: Proprietà CacheSize (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CacheSize
helpviewer_keywords:
- CacheSize property [ADO]
ms.assetid: 49dc9a49-af7b-433b-be36-7a14ca984fb7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6b33ef7eb4bae796fa2b2da59a7b1dc805d739e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920338"
---
# <a name="cachesize-property-ado"></a>Proprietà CacheSize (ADO)
Indica il numero di record di un oggetto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) memorizzati nella cache localmente in memoria.  
  
## <a name="settings-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta o restituisce un valore **Long** che deve essere maggiore di 0. Il valore predefinito è 1.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare la proprietà **CacheSize** per controllare il numero di record da recuperare contemporaneamente nella memoria locale del provider. Se, ad esempio, **CacheSize** è 10, dopo la prima apertura dell'oggetto **Recordset** , il provider recupera i primi 10 record nella memoria locale. Quando si sposta l'oggetto **Recordset** , il provider restituisce i dati dal buffer di memoria locale. Non appena si passa oltre l'ultimo record nella cache, il provider recupera i 10 record successivi dall'origine dati nella cache.  
  
> [!NOTE]
>  **CacheSize** è basato sulla proprietà massima specifica del provider di **righe aperte** (nella raccolta **Properties** dell'oggetto **Recordset** ). Non è possibile impostare **CacheSize** su un valore maggiore del **numero massimo di righe aperte**. Per modificare il numero di righe che possono essere aperte dal provider, impostare il numero **massimo di righe aperte**.  
  
 Il valore di **CacheSize** può essere regolato durante il ciclo di vita dell'oggetto **Recordset** , ma la modifica di questo valore influisca solo sul numero di record nella cache dopo i successivi recuperi dall'origine dati. La modifica del valore della proprietà da solo non comporterà la modifica del contenuto corrente della cache.  
  
 Se il numero di record da recuperare è inferiore a quello specificato da **CacheSize** , il provider restituisce i record rimanenti e non si verifica alcun errore.  
  
 Un'impostazione **CacheSize** pari a zero non è consentita e restituisce un errore.  
  
 I record recuperati dalla cache non riflettono le modifiche simultanee apportate da altri utenti ai dati di origine. Per forzare un aggiornamento di tutti i dati memorizzati nella cache, usare il metodo [Resync](../../../ado/reference/ado-api/resync-method.md) .  
  
 Se **CacheSize** è impostato su un valore maggiore di uno, i metodi di navigazione ([Move](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext e MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) possono comportare la navigazione su un record eliminato, se l'eliminazione viene eseguita dopo il recupero dei record. Dopo il recupero iniziale, le eliminazioni successive non verranno riflesse nella cache dei dati fino a quando non si tenta di accedere a un valore di dati da una riga eliminata. Tuttavia, l'impostazione di **CacheSize** su uno Elimina questo problema perché non è possibile recuperare le righe eliminate.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà CacheSize (VB)](../../../ado/reference/ado-api/cachesize-property-example-vb.md)   
 [Esempio di proprietà CacheSize (VC + +)](../../../ado/reference/ado-api/cachesize-property-example-vc.md)   
 [Esempio della proprietà CacheSize (JScript)](../../../ado/reference/ado-api/cachesize-property-example-jscript.md)
