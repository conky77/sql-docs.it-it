---
title: SESSION_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/23/2018
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
author: VanMSFT
ms.author: vanto
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3b63cbd1498021fdf9ed8418c3ff36ddec9143f0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68022235"
---
# <a name="session_id-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Restituisce l'ID della sessione [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore **nvarchar(32)** .  
  
## <a name="general-remarks"></a>Osservazioni generali  
 L'ID sessione viene assegnato a ogni connessione utente al momento dell'attivazione. Viene mantenuto per la durata della connessione. Al termine della connessione, l'ID sessione viene rilasciato.  
  
 L'ID sessione inizia con i caratteri alfabetici 'SID'. L'impostazione rileva le maiuscole e deve essere scritta in maiuscolo quando l'ID sessione viene usato nei comandi [!INCLUDE[DWsql](../../includes/dwsql-md.md)].  
  
 È possibile eseguire una query sulla visualizzazione [sys.dm_pdw_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md) per recuperare le stesse informazioni ottenute con questa funzione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il nome dell'ID sessione corrente.  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [VERSION &#40;SQL Data Warehouse&#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  
