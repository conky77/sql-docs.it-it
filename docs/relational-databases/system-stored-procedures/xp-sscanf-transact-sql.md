---
title: xp_sscanf (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_sscanf_TSQL
- xp_sscanf
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sscanf
ms.assetid: 619a9df1-7008-407e-a75a-bc6f851454a8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e46fe3243f39f8783743bf11e08b6368d67116eb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091905"
---
# <a name="xp_sscanf-transact-sql"></a>xp_sscanf (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legge i dati da una stringa nelle posizioni specificate da ciascun argomento di formato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
xp_sscanf { string OUTPUT , format } [ ,argument [ ,...n ] ]   
```  
  
## <a name="arguments"></a>Argomenti  
 **stringa**  
 Stringa di caratteri da cui leggere i valori dell'argomento.  
  
 OUTPUT  
 Quando specificato, inserisce il valore dell' *argomento* nel parametro di output.  
  
 *formato*  
 È una stringa di caratteri formattata simile a quella supportata dalla funzione **sscanf** del linguaggio C. Attualmente è supportato solo l'argomento di formato %.  
  
 *argomento*  
 Variabile **varchar** impostata sul valore dell'argomento di *formato* corrispondente.  
  
 *n*  
 Segnaposto che indica la possibilità di specificare un massimo di 50 argomenti.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
 **xp_sscanf** restituisce il messaggio seguente:  
  
 `Command(s) completed successfully.`  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la stored procedure estesa `xp_sscanf` viene utilizzata per estrarre due valori da una stringa di origine in base alle loro posizioni nel formato di tale stringa.  
  
```  
DECLARE @filename varchar (20), @message varchar (20);  
EXEC xp_sscanf 'sync -b -fproducts10.tmp -rrandom', 'sync -b -f%s -r%s',   
  @filename OUTPUT, @message OUTPUT;  
SELECT @filename, @message;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------- --------------------   
products10.tmp        random  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure estese generali &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_sprintf &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/xp-sprintf-transact-sql.md)  
  
  
