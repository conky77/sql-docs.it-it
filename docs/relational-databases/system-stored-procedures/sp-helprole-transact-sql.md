---
title: sp_helprole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helprole_TSQL
- sp_helprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprole
ms.assetid: b023103f-ccf3-44e2-b418-4be9bdd49f4a
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4caa5d8ab850c06aec62b84088463dc21bb40ea2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997501"
---
# <a name="sp_helprole-transact-sql"></a>sp_helprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sui ruoli del database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helprole [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @rolename = ] 'role'`Nome di un ruolo nel database corrente. *Role* è di **tipo sysname**e il valore predefinito è null. il *ruolo* deve esistere nel database corrente. Se *Role* non è specificato, vengono restituite informazioni su tutti i ruoli nel database corrente.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**RoleName**|**sysname**|Nome del ruolo nel database corrente.|  
|**RoleId**|**smallint**|ID di **roleName**.|  
|**IsAppRole**|**int**|0 = **roleName** non è un ruolo applicazione.<br /><br /> 1 = **roleName** è un ruolo applicazione.|  
  
## <a name="remarks"></a>Osservazioni  
 Per visualizzare le autorizzazioni associate al ruolo, utilizzare **sp_helprotect**. Per visualizzare i membri di un ruolo del database, utilizzare **sp_helprolemember**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la query restituisce tutti i ruoli nel database corrente.  
  
```  
EXEC sp_helprole  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sicurezza &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Ruoli a livello di server](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Ruoli a livello di database](../../relational-databases/security/authentication-access/database-level-roles.md)   
 [sp_addapprole &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [sp_addrole &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [sp_droprole &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_helprolemember &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [sp_helpsrvrolemember &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
