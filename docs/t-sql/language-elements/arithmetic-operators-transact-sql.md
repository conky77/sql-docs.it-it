---
title: Operatori aritmetici (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], arithmetic
- arithmetic operators
- math operations [Transact-SQL]
ms.assetid: a41b92a5-1061-4e4d-bb3b-a180b73c88fa
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 94d617f0da60b73ecfc7a0dcdd4530a3a36f3ca7
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "67927361"
---
# <a name="arithmetic-operators-transact-sql"></a>Operatori aritmetici (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Gli operatori aritmetici eseguono operazioni matematiche su due espressioni di uno o più tipi di dati appartenenti alla categoria dei tipi di dati numerici. Per altre informazioni sulle categorie dei tipi di dati, vedere [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Operatore|Significato|  
|--------------|-------------|  
|[+ (addizione)](../../t-sql/language-elements/add-transact-sql.md)|Addizione|  
|[- (sottrazione)](../../t-sql/language-elements/subtract-transact-sql.md)|Sottrazione|  
|[* (Moltiplicazione)](../../t-sql/language-elements/multiply-transact-sql.md)|Moltiplicazione|  
|[/ (divisione)](../../t-sql/language-elements/divide-transact-sql.md)|Divisione|  
|[% (modulo)](../../t-sql/language-elements/modulo-transact-sql.md)|Restituisce il resto intero di una divisione, ad esempio 12 % 5 = 2 perché il resto di 12 diviso 5 è 2|  
  
Gli operatori di addizione (+) e sottrazione (-) possono anche essere usati per eseguire operazioni aritmetiche su valori **datetime** e **smalldatetime**.  
  
Per altre informazioni sulla precisione e la scala del risultato di un'operazione aritmetica, vedere [Precisione, scala e lunghezza &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Funzioni matematiche &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
[Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  
