---
title: FrameWindowVisible | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: fd09d5d20b2a84050390c3e131265feddc09a409
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63285598"
---
# <a name="framewindowvisible"></a>FrameWindowVisible
  Proprietà che specifica se una data cornice di finestra è visibile. Il metodo helper viene utilizzato dal codice gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL WINAPI IsFrameWindowVisible(IVsWindowFrame* frame)  
{  
    if (NULL == frame)  
    {  
        return FALSE;  
    }  
  
    return S_OK == frame->IsVisible();  
}  
```  
  
#### <a name="parameters"></a>Parametri  
 *frame*  
  
 Puntatore IVsWindowFrame* a Visual Studio WindowFrame.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore booleano che specifica se la cornice della finestra specificata da *frame* è visibile.  
  

<!-- Necessary temporarily. GeneMi, 2018-05-01.
     But 'release-sql2014-migration' should win the Conflict Resolution later in May, because this will then be a good link!
## See Also  
 [SqlToolsVSNativeHelpers](sqltoolsvsnativehelpers.md)  
-->
  
  
