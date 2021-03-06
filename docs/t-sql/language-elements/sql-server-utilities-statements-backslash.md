---
title: Barra rovesciata (continuazione di riga) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/25/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '\_TSQL'
- '\'
dev_langs:
- TSQL
helpviewer_keywords:
- backwhack
- backslash
- escape character
- hack character
- '\ (backslash)'
- backslant
- bash
- reverse slant
- slosh
- reversed virgule
- line continuation character
- reverse solidus
ms.assetid: c97fbb20-3d12-4d0b-9b52-62a229bc83c0
author: rothja
ms.author: jroth
ms.openlocfilehash: 54e1dcd9735610f7cc8f109f00aa56fa7728ce04
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68495439"
---
# <a name="backslash-line-continuation-transact-sql"></a>Barra rovesciata (continuazione di riga) (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

`\` suddivide una stringa estesa di tipo costante, di caratteri o binaria in due o più righe per una maggiore leggibilità.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
## <a name="arguments"></a>Argomenti  
 \<prima sezione di stringa>  
 Inizio di una stringa.  
  
 \<sezione successiva di stringa>  
 Continuazione di una stringa.  
  
## <a name="remarks"></a>Osservazioni  
Questo comando restituisce le prime sezioni e quelle successive della stringa come un'unica stringa, senza la barra rovesciata. La nuova riga dopo la barra rovesciata deve essere un carattere di avanzamento riga (U+000A) o una combinazione di ritorno a capo (U+000D) e avanzamento riga (U+000A), in quest'ordine. 

## <a name="examples"></a>Esempi  

### <a name="a-splitting-a-character-string"></a>R. Suddivisione di una stringa di caratteri  

Nell'esempio seguente vengono usati una barra rovesciata e un ritorno a capo per suddividere una stringa di caratteri in due righe.  
  
```  
SELECT 'abc\  
def' AS [ColumnResult];  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 abcdef
 ```    

### <a name="b-splitting-a-binary-string"></a>B. Suddivisione di una stringa binaria  

Nell'esempio seguente vengono usati una barra rovesciata e un ritorno a capo per suddividere una stringa binaria in due righe.  

```  
SELECT 0xabc\
def AS [ColumnResult];  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 0xABCDEF
 ```    

## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [&#40;divisione&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/divide-transact-sql.md)   
 [&#40;assegnazione di divisione&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [Operatori composti &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  
