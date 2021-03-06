---
title: sys. foreign_keys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- foreign_keys
- sys.foreign_keys
- sys.foreign_keys_TSQL
- foreign_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.foreign_keys catalog view
ms.assetid: e960df1a-13fc-43ee-ba91-34c1b719ac2c
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b78466b0c2c20bc3b59fb372870bbad87aef0e74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133894"
---
# <a name="sysforeign_keys-transact-sql"></a>sys.foreign_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni oggetto che rappresenta un vincolo FOREIGN KEY, con **sys. Object. Type** = F.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**\<Colonne ereditate da sys. Objects>**||Per un elenco di colonne ereditate da questa vista, vedere [sys. objects &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**referenced_object_id**|**int**|ID dell'oggetto a cui viene fatto riferimento.|  
|**key_index_id**|**int**|ID della chiave di indice all'interno dell'oggetto a cui viene fatto riferimento.|  
|**is_disabled**|**bit**|Il vincolo FOREIGN KEY è disabilitato.|  
|**is_not_for_replication**|**bit**|Il vincolo FOREIGN KEY è stato creato con l'opzione NOT FOR REPLICATION.|  
|**is_not_trusted**|**bit**|Il vincolo FOREIGN KEY non è stato verificato dal sistema.|  
|**delete_referential_action**|**tinyint**|Operazione referenziale dichiarata per il vincolo FOREIGN KEY in caso di eliminazione.<br /><br /> 0 = Nessuna operazione<br /><br /> 1 = Propagazione<br /><br /> 2 = Impostazione su Null<br /><br /> 3 = Impostazione del valore predefinito|  
|**delete_referential_action_desc**|**nvarchar (60)**|Descrizione dell'operazione referenziale dichiarata per il vincolo FOREIGN KEY in caso di eliminazione:<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**update_referential_action**|**tinyint**|Operazione referenziale dichiarata per il vincolo FOREIGN KEY in caso di aggiornamento.<br /><br /> 0 = Nessuna operazione<br /><br /> 1 = Propagazione<br /><br /> 2 = Impostazione su Null<br /><br /> 3 = Impostazione del valore predefinito|  
|**update_referential_action_desc**|**nvarchar (60)**|Descrizione dell'operazione referenziale dichiarata per il vincolo FOREIGN KEY in caso di aggiornamento:<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**is_system_named**|**bit**|1 = Nome generato dal sistema.<br /><br /> 0 = Nome specificato dall'utente.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo oggetti &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query sul catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
