---
title: sp_addextendedproc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0bc8ea22699762927a026ae4cc811500c193555c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68072750"
---
# <a name="sp_addextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Registra il nome di un nuovo stored procedure esteso a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Usare invece l' [integrazione con CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @functname = ] 'procedure'`Nome della funzione da chiamare all'interno della libreria di collegamento dinamico (DLL). la *routine* è di **tipo nvarchar (517)** e non prevede alcun valore predefinito. Facoltativamente, la *procedura* può includere il nome del proprietario nel formato *owner. Function*.  
  
`[ @dllname = ] 'dll'`Nome della DLL che contiene la funzione. la *dll* è **varchar (255)** e non prevede alcun valore predefinito. È consigliabile specificare il percorso completo della DLL.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Dopo la creazione di un stored procedure esteso, è necessario aggiungerlo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a utilizzando **sp_addextendedproc**. Per ulteriori informazioni, vedere [aggiunta di una stored procedure estesa a SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md).  
  
 Questa procedura può essere eseguita solo nel database **Master** . Per eseguire un stored procedure esteso da un database diverso da **Master**, qualificare il nome del stored procedure esteso con **Master**.  
  
 **sp_addextendedproc** aggiunge voci alla vista del catalogo [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) , registrando il nome della nuova stored procedure estesa con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Viene inoltre aggiunta una voce nella vista del catalogo [sys. extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) .  
  
> [!IMPORTANT]  
>  Le DLL esistenti non registrate con un percorso completo non funzionano dopo l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per risolvere il problema, utilizzare **sp_dropextendedproc** per annullare la registrazione della dll e quindi registrarla nuovamente con **sp_addextendedproc**, specificando il percorso completo.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_addextendedproc**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aggiunto il **xp_hello** stored procedure esteso.  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [CONCEDERE &#40;&#41;Transact-SQL](../../t-sql/statements/grant-transact-sql.md)   
 [Revoke &#40;&#41;Transact-SQL](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
