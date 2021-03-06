---
title: sys. column_store_dictionaries (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3d69a2355f18a162f3e7a6b76b07bbb7cd6a597a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "75656618"
---
# <a name="syscolumn_store_dictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni dizionario utilizzato negli indici columnstore con ottimizzazione per la memoria xVelocity. I dizionari vengono utilizzati per codificare alcuni tipi di dati, ma non tutti. Pertanto non tutte le colonne in un indice columnstore contengono dizionari. Un dizionario può essere presente come dizionario primario (per tutti i segmenti) e possibilmente per altri dizionari secondari utilizzati per un subset di segmenti della colonna.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|ID dell'indice heap o albero B (HoBT) per la tabella con l'indice columnstore.|  
|**column_id**|**int**|ID della colonna columnstore che inizia con 1. La prima colonna contiene ID = 1, la seconda colonna ha ID = 2 e così via.|  
|**dictionary_id**|**int**|Possono essere presenti due tipi di dizionari, globale e locale, associati a un segmento di colonna. Un dictionary_id di 0 rappresenta il dizionario globale condiviso tra tutti i segmenti di colonna (uno per ogni gruppo di righe) per la colonna.|  
|**Versione**|**int**|Versione del formato del dizionario.|  
|**tipo**|**int**|Tipo di dizionario:<br /><br /> 1: dizionario hash contenente valori **int**<br /><br /> 2-non utilizzato<br /><br /> 3: dizionario hash contenente valori stringa<br /><br /> 4: dizionario hash contenente valori **float**<br /><br /> Per altre informazioni sui dizionari, vedere [Guida agli indici columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md).|  
|**last_id**|**int**|L'ultimo ID dati nel dizionario.|  
|**entry_count**|**bigint**|Numero di voci nel dizionario.|  
|**on_disk_size**|**bigint**|Dimensioni del dizionario in byte.|  
|**partition_id**|**bigint**|Indica l'ID della partizione. Valore univoco all'interno di un database.|  
  
## <a name="permissions"></a>Autorizzazioni  
È richiesta l'autorizzazione `VIEW DEFINITION` per la tabella. Le colonne seguenti restituiscono null a meno che l'utente `SELECT` non disponga anche delle autorizzazioni: last_id, entry_count, data_ptr.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo oggetti &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query sul catalogo di sistema SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys. Columns &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. all_columns &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys. computed_columns &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Guida agli indici columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [Guida agli indici columnstore](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys. column_store_segments &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

