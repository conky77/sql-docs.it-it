---
title: Raccolta Fields (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields
- Recordset15::Fields
- _Record::Fields
helpviewer_keywords:
- Fields collection [ADO]
ms.assetid: 7c371474-b88f-4730-afa5-44163a0488d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9c9216ee655e371633837c5653ebac56fac1a782
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918708"
---
# <a name="fields-collection-ado"></a>Raccolta Fields (ADO)
Contiene tutti gli oggetti [campo](../../../ado/reference/ado-api/field-object.md) di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) o di un oggetto [record](../../../ado/reference/ado-api/record-object-ado.md) .  
  
## <a name="remarks"></a>Osservazioni  
 Un oggetto **Recordset** include una raccolta **Fields** costituita da oggetti **Field** . Ogni oggetto **campo** corrisponde a una colonna nel **Recordset**. È possibile popolare la raccolta **Fields** prima di aprire il **Recordset** chiamando il metodo [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) sulla raccolta.  
  
> [!NOTE]
>  Per una spiegazione più dettagliata dell'uso di oggetti **campo** , vedere l'argomento oggetto **campo** .  
  
 La raccolta **Fields** include un metodo [Append](../../../ado/reference/ado-api/append-method-ado.md) , che consente di creare e aggiungere in modo provvisorio un oggetto **campo** alla raccolta e un metodo **Update** , che finalizza eventuali aggiunte o eliminazioni.  
  
 Un oggetto **record** dispone di due campi speciali che possono essere indicizzati con costanti [FieldEnum](../../../ado/reference/ado-api/fieldenum.md) . Una costante accede a un campo contenente il flusso predefinito per il **record**e l'altro accede a un campo contenente la stringa URL assoluta per il **record**.  
  
 Alcuni provider, ad esempio il [provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), possono popolare la **raccolta Fields** con un subset di campi disponibili per il **record** o il **Recordset**. Gli altri campi non verranno aggiunti alla raccolta fino a quando non vi viene fatto riferimento in base al nome o indicizzati dal codice.  
  
 Se si tenta di fare riferimento a un campo inesistente in base al nome, verrà aggiunto un nuovo oggetto **campo** alla raccolta **Fields** con [lo stato](../../../ado/reference/ado-api/status-property-ado-field.md) **adFieldPendingInsert**. Quando si chiama [Update](../../../ado/reference/ado-api/update-method.md), ADO creerà un nuovo campo nell'origine dati, se consentito dal provider.  
  
 Questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi della raccolta Fields](../../../ado/reference/ado-api/fields-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Field](../../../ado/reference/ado-api/field-object.md)
