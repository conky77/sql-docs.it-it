---
title: SQLTables (driver Excel) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 89157178aa9c134bdb1b9518343007adb1e1e05f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132417"
---
# <a name="sqltables-excel-driver"></a>SQLTables (driver Excel)
> [!NOTE]  
>  In questo argomento vengono fornite informazioni specifiche del driver di Excel. Per informazioni generali su questa funzione, vedere l'argomento appropriato in informazioni di [riferimento sulle API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argomento|Commenti|  
|--------------|--------------|  
|*szTableOwner*|L'unico argomento valido per *szTableOwner* è null perché nessuno dei driver supporta i nomi di proprietario. Con *szTableOwner* impostato su null, vengono restituite tutte le tabelle. Nella colonna TABLE_OWNER viene restituito NULL.|  
|*szTableQualifier*|Quando si utilizza il driver Microsoft Excel 3,0 o 4,0, se si chiama **SQLTables** con un valore per *szTableQualifier* che non corrisponde al nome di una tabella esistente, il driver creerà una tabella con tale nome.<br /><br /> Nella colonna TABLE_QUALIFIER **SQLTables** restituirà il percorso di una directory.|  
|*SzTableType*|Per Microsoft Excel 3,0 o 4,0, "TABLE" è l'unico tipo di tabella supportato.<br /><br /> Per le versioni più recenti dei file di Microsoft Excel, viene restituito "tabella di sistema" per i nomi dei fogli (tabelle con una "$" alla fine) e "TABLE" viene restituito per le tabelle nei fogli di lavoro.|
