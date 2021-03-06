---
title: sys. Triggers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- triggers
- triggers_TSQL
- sys.triggers
- sys.triggers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.triggers catalog view
ms.assetid: cefa4fc4-b8b9-4cd7-b124-eed5283acbfc
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 33eb5a1c4176041d64ba60a3a684b75bc4816350
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091935"
---
# <a name="systriggers-transact-sql"></a>sys.triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni oggetto che è un trigger di tipo TR o TA. I nomi dei trigger DML sono con ambito schema e, pertanto, sono visibili in **sys. Objects**. I nomi di trigger DDL sono definiti a livello di ambito rispetto all'entità padre e sono visibili solo in questa vista.  
  
 Le colonne **parent_class** e **Name** identificano in modo univoco il trigger nel database.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**nome**|**sysname**|Nome del trigger. I nomi di trigger DML sono definiti a livello di ambito dello schema. I nomi di trigger DDL sono definiti a livello di ambito rispetto all'entità padre.|  
|**object_id**|**int**|Numero di identificazione dell'oggetto. Valore univoco all'interno di un database.|  
|**parent_class**|**tinyint**|Classe dell'entità padre del trigger.<br /><br /> 0 = Database per i trigger DDL.<br /><br /> 1 = Oggetto o colonna per i trigger DML.|  
|**parent_class_desc**|**nvarchar (60)**|Descrizione della classe padre del trigger.<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN|  
|**parent_id**|**int**|ID dell'entità padre del trigger. I possibili valori sono i seguenti:<br /><br /> 0 = Trigger che hanno come entità padre un database.<br /><br /> Per i trigger DML, questo è il **object_id** della tabella o della vista in cui è definito il trigger DML.|  
|**tipo**|**carattere (2)**|Tipo di oggetto:<br /><br /> TA = Trigger di assembly (CLR)<br /><br /> TR = trigger SQL|  
|**type_desc**|**nvarchar (60)**|Descrizione del tipo di oggetto.<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|Data di creazione del trigger.|  
|**modify_date**|**datetime**|Data dell'ultima modifica apportata all'oggetto mediante un'istruzione ALTER.|  
|**is_ms_shipped**|**bit**|Trigger creato per conto dell'utente da parte di un componente interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**is_disabled**|**bit**|Trigger disabilitato.|  
|**is_not_for_replication**|**bit**|Trigger creato con l'opzione NOT FOR REPLICATION.|  
|**is_instead_of_trigger**|**bit**|1 = Trigger INSTEAD OF<br /><br /> 0 = Trigger AFTER|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
