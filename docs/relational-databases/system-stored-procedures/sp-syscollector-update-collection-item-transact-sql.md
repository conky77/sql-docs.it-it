---
title: sp_syscollector_update_collection_item (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collection_item
- sp_syscollector_update_collection_item_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_update_collection_item
ms.assetid: 7a0d36c8-c6e9-431d-a5a4-6c1802bce846
author: stevestein
ms.author: sstein
ms.openlocfilehash: 791c20214ff3eda4b5bb1f2bd3214b25ea972d74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68010552"
---
# <a name="sp_syscollector_update_collection_item-transact-sql"></a>sp_syscollector_update_collection_item (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di rinominare un elemento della raccolta definito dall'utente o di modificarne le proprietà.  
  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syscollector_update_collection_item   
      [ [ @collection_item_id = ] collection_item_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @new_name = ] 'new_name' ]  
    , [ [ @frequency = ] frequency ]  
    , [ [ @parameters = ] 'parameters' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @collection_item_id = ] *collection_item_id*  
 Identificatore univoco che identifica l'elemento della raccolta. *collection_item_id* è di **tipo int** e il valore predefinito è null. *collection_item_id* deve avere un valore se il *nome* è null.  
  
 [ @name = ] '*Name*'  
 Nome dell'elemento della raccolta. *Name* è di **tipo sysname** e il valore predefinito è null. Se *collection_item_id* è null, il *nome* deve avere un valore.  
  
 [ @new_name = ] '*new_name*'  
 Nuovo nome per l'elemento della raccolta. *new_name* è di **tipo sysname**e, se utilizzato, non può essere una stringa vuota.  
  
 *new_name* deve essere univoco. Per un elenco dei nomi degli elementi della raccolta correnti, eseguire una query sulla vista di sistema syscollector_collection_items.  
  
 [ @frequency = ] *frequenza* di  
 Frequenza, espressa in secondi, con cui vengono raccolti i dati da questo elemento della raccolta. *Frequency* è di **tipo int**e il valore predefinito è 5, ovvero il valore minimo che è possibile specificare.  
  
 [ @parameters = ] '*Parameters*'  
 Parametri di input per l'elemento della raccolta. *Parameters* è di **XML** e il valore predefinito è null. Lo schema dei *parametri* deve corrispondere allo schema dei parametri del tipo di agente di raccolta.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Se il set di raccolta è impostato sulla modalità non in cache, la modifica della frequenza viene ignorata in quanto in questa modalità la raccolta e il caricamento dei dati vengono eseguiti in base alla pianificazione specificata per il set di raccolta. Per visualizzare lo stato del set di raccolta, eseguire la query seguente. Sostituire `<collection_item_id>` con l'ID dell'elemento della raccolta da aggiornare.  
  
```  
USE msdb;  
GO  
SELECT cs.collection_set_id, collection_set_uid, cs.name   
    ,'is running' = CASE WHEN is_running =  0 THEN 'No' ELSE 'Yes' END  
    ,'cache mode' = CASE WHEN collection_mode = 0 THEN 'Cached mode' ELSE 'Non-cached mode' END  
FROM syscollector_collection_sets AS cs  
JOIN syscollector_collection_items AS ci   
ON ci.collection_set_id = cs.collection_set_id  
WHERE collection_item_id = <collection_item_id>;  
```  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa procedura, è necessaria l'appartenenza al ruolo predefinito del database dc_admin o dc_operator (con autorizzazione EXECUTE). Anche se dc_operator è in grado di eseguire questa stored procedure, i membri di questo ruolo possono modificare solo determinate proprietà. Le proprietà seguenti possono essere modificate solo da dc_admin:  
  
-   @new_name  
  
-   @parameters  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti sono basati sull'elemento della raccolta creato nell'esempio definito in [sp_syscollector_create_collection_item &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md).  
  
### <a name="a-changing-the-collection-frequency"></a>R. Modifica della frequenza di raccolta  
 Nell'esempio seguente viene modificata la frequenza di raccolta per l'elemento della raccolta specificato.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@name = N'My custom TSQL query collector item',  
@frequency = 3000;  
GO  
```  
  
### <a name="b-renaming-a-collection-item"></a>B. Ridenominazione di un elemento della raccolta  
 Nell'esempio seguente viene rinominato un elemento della raccolta.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@name = N'My custom TSQL query collector item',  
@new_name = N'My modified TSQL item';  
GO  
```  
  
### <a name="c-changing-the-parameters-of-a-collection-item"></a>C. Modifica dei parametri di un elemento della raccolta  
 Nell'esempio seguente vengono modificati i parametri associati all'elemento della raccolta. L'istruzione definita all'interno dell'attributo `<Value>` viene modificata e l'attributo `UseSystemDatabases` viene impostato su false. Per visualizzare i parametri correnti per questo elemento, eseguire una query sulla colonna dei parametri nella vista di sistema syscollector_collection_items. Potrebbe essere necessario modificare il valore per `@collection_item_id`.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@collection_item_id = 9,   
@parameters = '  
    \<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
        <Query>  
            <Value>SELECT * FROM sys.dm_db_index_usage_stats</Value>  
            <OutputTable>MyOutputTable</OutputTable>  
        </Query>  
        <Databases>  
            <Database> UseSystemDatabases = "false"   
                       UseUserDatabases = "true"</Database>  
        </Databases>  
    \</ns:TSQLQueryCollector>';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_create_collection_item &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md)   
 [syscollector_collection_items &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)  
  
  
