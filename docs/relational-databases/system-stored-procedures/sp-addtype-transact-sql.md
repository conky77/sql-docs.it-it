---
title: sp_addtype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addtype
- sp_addtype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addtype
ms.assetid: ed72cd8e-5ff7-4084-8458-2d8ed279d817
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab825ce5eb1310f3ff502965e409731b8741932e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72305133"
---
# <a name="sp_addtype-transact-sql"></a>sp_addtype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un tipo di dati alias.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]In alternativa, usare [Create type](../../t-sql/statements/create-type-transact-sql.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addtype [ @typename = ] type,   
    [ @phystype = ] system_data_type   
    [ , [ @nulltype = ] 'null_type' ] ;  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @typename = ] type`Nome del tipo di dati alias. I nomi dei tipi di dati alias devono rispettare le regole per gli [identificatori](../../relational-databases/databases/database-identifiers.md) e devono essere univoci in ogni database. *Type* è di tipo **sysname**e non prevede alcun valore predefinito.  
  
`[ @phystype = ] system_data_type`Tipo di dati fisico o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornito su cui si basa il tipo di dati alias. *system_data_type* è di **tipo sysname**e non prevede alcun valore predefinito. i possibili valori sono i seguenti:  
  
||||  
|-|-|-|  
|**bigint**|**binary(n)**|**bit**|  
|**char(n)**|**datetime**|**decimal**|  
|**float**|**immagine**|**int**|  
|**money**|**nchar(n)**|**ntext**|  
|**numerico**|**nvarchar(n)**|**reale**|  
|**smalldatetime**|**smallint**|**SMALLMONEY**|  
|**sql_variant**|**text**|**tinyint**|  
|**uniqueidentifier**|**varbinary(n)**|**varchar(n)**|  
  
 È necessario racchiudere tra virgolette tutti i parametri che includono spazi vuoti o segni di punteggiatura. Per ulteriori informazioni sui tipi di dati disponibili, vedere [tipi di dati &#40;&#41;Transact-SQL ](../../t-sql/data-types/data-types-transact-sql.md).  
  
 *n*  
 Valore intero non negativo che indica la lunghezza del tipo di dati scelto.  
  
 *P*  
 Valore intero non negativo che indica il numero massimo di cifre decimali che è possibile archiviare sia a sinistra che a destra del separatore decimale. Per altre informazioni, vedere [decimal e numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *s*  
 Valore intero non negativo che indica il numero massimo di cifre decimali che è possibile archiviare a destra del separatore decimale. Deve essere minore o uguale al valore della precisione. Per altre informazioni, vedere [decimal e numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
`[ @nulltype = ] 'null_type'`Indica il modo in cui il tipo di dati alias gestisce i valori null. *null_type* è di tipo **varchar (** 8 **)** e il valore predefinito è null. deve essere racchiuso tra virgolette singole (' null ',' not null ' o ' nonull '). Se *null_type* non è definito in modo esplicito da **sp_addtype**, viene impostato sul supporto di valori null predefinito corrente. Utilizzare la funzione di sistema GETANSINULL per determinare l'impostazione predefinita corrente per il supporto dei valori Null. Questa impostazione può essere modificata tramite l'istruzione SET o ALTER DATABASE. L'impostazione relativa al supporto dei valori Null deve essere definita in modo esplicito. Se ** \@phystype** è **bit**e ** \@nulltype** non è specificato, il valore predefinito è not null.  
  
> [!NOTE]  
>  Il parametro *null_type* definisce solo l'impostazione predefinita relativa al supporto di valori null per questo tipo di dati. Se l'impostazione per il supporto dei valori Null viene definita in modo esplicito quando si utilizza il tipo di dati alias durante la creazione di tabelle, questo valore sarà prioritario rispetto all'impostazione predefinita. Per ulteriori informazioni, vedere [ALTER TABLE &#40;Transact-sql&#41;](../../t-sql/statements/alter-table-transact-sql.md) e [Create Table &#40;transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Il nome di un tipo di dati alias deve essere univoco all'interno del database, ma è possibile utilizzare la stessa definizione per tipi di dati alias con nomi diversi.  
  
 Eseguendo **sp_addtype** viene creato un tipo di dati alias visualizzato nella vista del catalogo **sys. Types** per un database specifico. Se il tipo di dati alias deve essere disponibile in tutti i nuovi database definiti dall'utente, aggiungerlo al **modello**. Dopo avere creato un tipo di dati alias, è possibile utilizzarlo in un'istruzione CREATE TABLE o ALTER TABLE e associarvi valori predefiniti e regole. Tutti i tipi di dati alias scalari creati utilizzando **sp_addtype** sono contenuti nello schema **dbo** .  
  
 I tipi di dati alias ereditano le regole di confronto predefinite del database. Le regole di confronto delle colonne e delle variabili dei tipi di alias sono [!INCLUDE[tsql](../../includes/tsql-md.md)] definite nelle istruzioni CREATE TABLE, ALTER TABLE e DECLARE @*local_variable* . Le modifiche apportate alle regole di confronto predefinite del database vengono applicate solo alle nuove colonne e variabili del tipo. Le regole di confronto delle colonne e delle variabili esistenti non vengono modificate.  
  
> [!IMPORTANT]  
>  Per motivi di compatibilità con le versioni precedenti, al ruolo del database **pubblico** viene concessa automaticamente l'autorizzazione REFERENCES per i tipi di dati alias creati utilizzando **sp_addtype**. Nota Quando i tipi di dati alias vengono creati usando l'istruzione CREATE TYPE invece di **sp_addtype**, non viene concessa tale concessione automatica.  
  
 I tipi di dati alias non possono essere definiti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando i tipi di dati **timestamp**, **Table**, **XML**, **varchar (max)**, **nvarchar (max)** o **varbinary (max)** .  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del database **db_owner** o **db_ddladmin** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-an-alias-data-type-that-does-not-allow-for-null-values"></a>R. Creazione di un tipo di dati alias che non consente valori Null  
 Nell'esempio seguente viene creato un tipo di dati `ssn` alias denominato (Social Security Number) basato sul tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di dati **varchar** fornito da. Il tipo di dati `ssn` viene utilizzato per colonne contenenti numeri di previdenza sociale a 11 cifre (999-99-9999). Questa colonna non può contenere valori NULL.  
  
 Si noti che `varchar(11)` è racchiuso tra virgolette singole in quanto contiene segni di punteggiatura (le parentesi).  
  
```  
USE master;  
GO  
EXEC sp_addtype ssn, 'varchar(11)', 'NOT NULL';  
GO  
```  
  
### <a name="b-creating-an-alias-data-type-that-allows-for-null-values"></a>B. Creazione di un tipo di dati alias che consente valori Null  
 Nell'esempio seguente viene creato un tipo di dati alias basato sul tipo di dati `datetime` e denominato `birthday` che consente valori Null.  
  
```  
USE master;  
GO  
EXEC sp_addtype birthday, datetime, 'NULL';  
```  
  
### <a name="c-creating-additional-alias-data-types"></a>C. Creazione di tipi di dati alias aggiuntivi  
 Nell'esempio seguente vengono creati due tipi di dati alias aggiuntivi, `telephone` e `fax`, per i numeri di telefono e di fax nazionali e internazionali.  
  
```  
USE master;  
GO  
EXEC sp_addtype telephone, 'varchar(24)', 'NOT NULL';  
GO  
EXEC sp_addtype fax, 'varchar(24)', 'NULL';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di motore di database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Crea tipo &#40;&#41;Transact-SQL](../../t-sql/statements/create-type-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREARE una regola &#40;&#41;Transact-SQL](../../t-sql/statements/create-rule-transact-sql.md)   
 [sp_bindefault &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_bindrule &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_droptype &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)   
 [sp_rename &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindefault &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [sp_unbindrule &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
