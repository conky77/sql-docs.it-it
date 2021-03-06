---
title: Metodo sepermissions (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50a609d0cebe70ea5127ed448e57a70881e35097
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965220"
---
# <a name="setpermissions-method-adox"></a>Metodo SetPermissions (ADOX)
Specifica le autorizzazioni per un [gruppo](../../../ado/reference/adox-api/group-object-adox.md) o un [utente](../../../ado/reference/adox-api/user-object-adox.md) in un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Valore **stringa** che specifica il nome dell'oggetto per il quale impostare le autorizzazioni.  
  
 *ObjectType*  
 Valore **Long** che può essere una delle costanti [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) , che specifica il tipo dell'oggetto per il quale ottenere le autorizzazioni.  
  
 *Azione*  
 Valore **Long** che può essere una delle costanti [ActionEnum indicante](../../../ado/reference/adox-api/actionenum.md) che specifica il tipo di azione da eseguire durante l'impostazione delle autorizzazioni.  
  
 *Diritti*  
 Valore **Long** che può essere una maschera di maschera di una o più costanti [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) , che indica i diritti da impostare.  
  
 *Ereditare*  
 Facoltativa. Valore **Long** che può essere una delle costanti [InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md) , che specifica il modo in cui gli oggetti erediteranno tali autorizzazioni. Il valore predefinito è **adInheritNone**.  
  
 *ObjectTypeId*  
 Facoltativa. Valore **Variant** che specifica il GUID per un tipo di oggetto provider non definito dalla specifica OLE DB. Questo parametro è obbligatorio se *ObjectType* è impostato su **adPermObjProviderSpecific**; in caso contrario, non viene utilizzato.  
  
## <a name="remarks"></a>Osservazioni  
 Se il provider non supporta l'impostazione dei diritti di accesso per gruppi o utenti, si verificherà un errore.  
  
> [!NOTE]
>  Quando si richiamano le **autorizzazioni**, l'impostazione di Actions su **adAccessRevoke** esegue l'override di qualsiasi impostazione del parametro *Rights* . Non impostare *azioni* su **adAccessRevoke** se si desidera che i diritti specificati nel parametro *Rights* abbiano effetto.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Oggetto User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi GetPermissions e sepermissions (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [Metodo GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Proprietà Name (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
