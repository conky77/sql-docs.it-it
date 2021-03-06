---
title: SQLGetDescField e SQLGetDescRec (libreria di cursori) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetDescField function [ODBC], Cursor Library
- SQLGetDescRec function [ODBC], Cursor Library
ms.assetid: 1a801f22-6fea-48aa-a723-3187a2ad852b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 853a364b61b63d58da93111c75db0d7d723ee49b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073907"
---
# <a name="sqlgetdescfield-and-sqlgetdescrec-cursor-library"></a>SQLGetDescField e SQLGetDescRec (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Microsoft consiglia di utilizzare la funzionalità di cursore del driver.  
  
 In questo argomento viene illustrato l'utilizzo delle funzioni **SQLGetDescField** e **SQLGetDescRec** nella libreria di cursori. Per informazioni generali su queste funzioni, vedere [funzione SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md) e [funzione SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md).  
  
 La libreria di cursori esegue **SQLGetDescRec** per restituire i metadati per le colonne dei segnalibri. La libreria di cursori esegue **SQLGetDescField** per restituire gli stessi campi restituiti da **SQLGetDescRec**, che sono SQL_DESC_NAME, SQL_DESC_TYPE, SQL_DESC_DATETIME_INTERVAL_CODE, SQL_DESC_OCTET_LENGTH, SQL_DESC_PRECISION, SQL_DESC_SCALE e SQL_DESC_NULLABLE. Per coerenza, **SQLGetDescField** restituisce anche SQL_DESC_UNNAMED.  
  
 La libreria di cursori esegue **SQLGetDescField** quando viene chiamato per restituire il valore dei campi seguenti impostati per l'associazione di colonne di segnalibro: SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR e SQL_DESC_LENGTH.  
  
 La libreria di cursori esegue **SQLGetDescField** quando viene chiamato per restituire il valore del campo SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE o SQL_DESC_ROW_STATUS_PTR. Questi campi possono essere restituiti per qualsiasi riga, non solo per la riga del segnalibro.  
  
 Se un'applicazione chiama **SQLGetDescField** per restituire il valore di un campo diverso da quello indicato in precedenza, la libreria di cursori passa la chiamata al driver.
