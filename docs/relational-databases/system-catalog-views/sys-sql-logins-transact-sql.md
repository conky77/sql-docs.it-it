---
title: sys. sql_logins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 362ccc5c85523b3d37cb792a42e8be4cd87d7510
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108999"
---
# <a name="syssql_logins-transact-sql"></a>sys.sql_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Viene restituita una riga per ogni account di accesso con autenticazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**\<colonne ereditate>**|--|Eredita da **sys. server_principals**.|  
|**is_policy_checked**|**bit**|I criteri password vengono controllati.|  
|**is_expiration_checked**|**bit**|La scadenza delle password viene controllata.|  
|**password_hash**|**varbinary (256)**|Hash della password dell'account di accesso di SQL. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], le informazioni relative alle password archiviate vengono calcolate tramite SHA-512 della password salt.|  
  
 Per un elenco delle colonne ereditate da questa vista, vedere [sys. server_principals &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="remarks"></a>Osservazioni  
 Per visualizzare gli [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso con autenticazione di Windows e gli account di accesso con autenticazione di Windows, vedere [sys. Server_principals &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Se gli utenti del database indipendente sono abilitati, le connessioni possono essere effettuate senza account di accesso. Per identificare gli account, vedere [sys. database_principals &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Con qualsiasi account di accesso con autenticazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile visualizzare il relativo nome di account di accesso e l'account di accesso sa. Per visualizzare altri account di accesso, è richiesta l'autorizzazione ALTER ANY LOGIN o un'autorizzazione per l'account di accesso.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Criteri password](../../relational-databases/security/password-policy.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
