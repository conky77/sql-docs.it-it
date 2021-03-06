---
title: Funzioni di catalogo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 232d2e9b7e9eb695a40058075ea511392e464a32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064404"
---
# <a name="catalog-functions"></a>Funzioni di catalogo
In tutti i database è presente una struttura che descrive la modalità di archiviazione dei dati nel database. Ad esempio, è possibile che un database di ordini di vendita semplice abbia la struttura mostrata nella figura seguente, in cui le colonne ID vengono utilizzate per collegare le tabelle.  
  
 ![Struttura di un database semplice](../../../odbc/reference/develop-app/media/pr19.gif "PR19")  
  
 Questa struttura, insieme ad altre informazioni, ad esempio i privilegi, è archiviata in un set di tabelle di sistema denominato catalogo del database *,* noto anche come *dizionario dei dati*.  
  
 Un'applicazione può individuare questa struttura tramite chiamate alle *funzioni di catalogo*. Le funzioni di catalogo restituiscono informazioni nei set di risultati e vengono in genere implementate tramite istruzioni **Select** per le tabelle nel catalogo. Un'applicazione potrebbe ad esempio richiedere un set di risultati contenente informazioni su tutte le tabelle del sistema o tutte le colonne di una particolare tabella.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Utilizzi dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Funzioni di catalogo in ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
