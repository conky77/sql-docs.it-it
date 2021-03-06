---
title: CLR strict security | Microsoft Docs
description: Come configurare CLR strict security in SQL Server
ms.custom: ''
ms.date: 06/20/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- clr strict security
- clr_strict_security_TSQL
- clr strict security
- strict_security_TSQL
helpviewer_keywords:
- assemblies [CLR integration], strick security
- clr strict security option
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4c77d87f1ffe0083662f9f4fcfe643de3359ea59
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68012966"
---
# <a name="clr-strict-security"></a>CLR strict security   
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Controlla l'interpretazione delle autorizzazioni `SAFE`, `EXTERNAL ACCESS` e `UNSAFE` in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].   

|valore |Descrizione | 
|----- |----- | 
|0 |Disabilitata: mantenuta per compatibilità con le versioni precedenti. Il valore `Disabled` non è consigliato. | 
|1 |Abiltata: indica a [!INCLUDE[ssde-md](../../includes/ssde-md.md)] di ignorare le informazioni `PERMISSION_SET` sugli assembly e di interpretarli sempre come `UNSAFE`.  `Enabled` è il valore predefinito di [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)]. | 

> [!WARNING]
>  CLR usa la Sicurezza dall'accesso di codice (CAS, Code Access Security) in .NET Framework, non più supportata come limite di sicurezza. Un assembly CLR creato con `PERMISSION_SET = SAFE` potrebbe essere in grado di accedere alle risorse di sistema esterne, chiamare codice non gestito e acquisire privilegi sysadmin. A partire da [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)], viene introdotta un'opzione `sp_configure` denominata `clr strict security` per migliorare la sicurezza degli assembly CLR. `clr strict security` è abilitata per impostazione predefinita e considera gli assembly CLR `SAFE` e `EXTERNAL_ACCESS` come se fossero contrassegnati `UNSAFE`. È possibile disabilitare l'opzione `clr strict security` per la compatibilità con le versioni precedenti, ma questa operazione è sconsigliata. Microsoft consiglia che tutti gli assembly siano firmati con un certificato o una chiave asimmetrica con un account di accesso corrispondente che disponga dell'autorizzazione `UNSAFE ASSEMBLY` nel database master. Gli amministratori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono anche aggiungere assembly a un elenco di assembly, considerato attendibile dal motore di database. Per altre, vedere [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md).

## <a name="remarks"></a>Osservazioni   

Quando abilitata, l'opzione `PERMISSION_SET` nelle istruzioni `CREATE ASSEMBLY` e `ALTER ASSEMBLY` viene ignorata durante l'esecuzione, ma le opzioni `PERMISSION_SET` vengono mantenute nei metadati. Ignorando l'opzione, si ridurranno al minimo le interruzioni nelle istruzioni di codice esistenti.

`CLR strict security` è di tipo `advanced option`.  

> [!IMPORTANT]
>  Dopo l'abilitazione di strict security, tutti gli assembly non firmati non verranno caricati. È necessario modificare oppure eliminare e ricreare ogni assembly in modo che sia firmato con un certificato o una chiave asimmetrica con un account di accesso corrispondente con l'autorizzazione `UNSAFE ASSEMBLY` nel server.

## <a name="permissions"></a>Autorizzazioni 

### <a name="to-change-this-option"></a>Per modificare questa opzione  
È richiesta l'autorizzazione `CONTROL SERVER` o l'appartenenza al ruolo predefinito del server `sysadmin`.

### <a name="to-create-an-clr-assembly"></a>Per creare un assembly CLR   
Sono necessarie le autorizzazioni seguenti per creare un assembly CLR con `CLR strict security` abilitata:

- L'utente deve disporre dell'autorizzazione `CREATE ASSEMBLY`  
- Inoltre, una delle condizioni seguenti deve essere rispettata:  
  - L'assembly è firmato con un certificato o una chiave asimmetrica con un account di accesso corrispondente con l'autorizzazione `UNSAFE ASSEMBLY` nel server. È consigliabile firmare l'assembly.  
  - La proprietà `TRUSTWORTHY` del database è impostata su `ON` e il database è di proprietà di un accesso che dispone dell'autorizzazione `UNSAFE ASSEMBLY` nel server. Questa opzione non è consigliata.  

  
## <a name="see-also"></a>Vedere anche  
  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Opzione di configurazione del server clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)
