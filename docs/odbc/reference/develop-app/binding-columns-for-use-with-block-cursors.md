---
title: Associazione di colonne da utilizzare con cursori a blocchi | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 827f6ddca12f15ce0bce1773b9cbe26fae5069dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106235"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>Associazione di colonne per l'uso con cursori rettangolari
Poiché i cursori a blocchi restituiscono più righe, le applicazioni che le utilizzano devono associare una matrice di variabili a ogni colonna anziché a una singola variabile. Queste matrici sono note collettivamente come buffer del *set di righe*. Di seguito sono riportati i due stili di associazione:  
  
-   Associare una matrice a ogni colonna. Questa operazione viene definita *associazione per colonna* perché ogni struttura di dati (matrice) contiene dati per una singola colonna.  
  
-   Definire una struttura per conservare i dati per un'intera riga e associare una matrice di queste strutture. Questa operazione viene definita *associazione per riga* perché ogni struttura di dati contiene i dati per una singola riga.  
  
 Quando l'applicazione associa singole variabili a colonne, chiama **SQLBindCol** per associare le matrici alle colonne. L'unica differenza consiste nel fatto che gli indirizzi passati sono indirizzi di matrice, non singoli indirizzi di variabili. L'applicazione imposta l'attributo dell'istruzione SQL_BIND_BY_COLUMN per specificare se utilizza l'associazione per colonna o per riga. La possibilità di utilizzare l'associazione per colonna o per riga è in gran parte una questione di preferenza dell'applicazione. L'associazione per riga potrebbe corrispondere più strettamente al layout di dati dell'applicazione. in questo caso, è possibile ottenere prestazioni migliori.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Associazione per colonna](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [Associazione per riga](../../../odbc/reference/develop-app/row-wise-binding.md)
