---
title: Opzione di configurazione del server Stored procedure estese di posta elettronica database | Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e16286e558d860a346ba8fff366009f064e65f91
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68011965"
---
# <a name="database-mail-xps-server-configuration-option"></a>Opzione di configurazione del server Database Mail XPs

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Usare l'opzione **Stored procedure estese di posta elettronica database** per abilitare Posta elettronica database nel server. I valori possibili sono:  
  
- `0`: Posta elettronica database non è disponibile (impostazione predefinita).  
  
- `1`: Posta elettronica database è disponibile.  
  
 L'impostazione diventa effettiva immediatamente e non richiede l'arresto e il riavvio del server.  
  
 Dopo aver abilitato Posta elettronica database, è necessario configurare un database host di Posta elettronica database per l'utilizzo di tale funzionalità.  
  
 La configurazione di Posta elettronica database tramite la **Configurazione guidata posta elettronica database** ne abilita le stored procedure estese nel database `msdb`. Se si usa la **Configurazione guidata posta elettronica database** non è necessario usare l'esempio `sp_configure` riportato di seguito.  
  
 L'impostazione dell'opzione **Stored procedure estese di posta elettronica database** su `0` impedisce l'avvio di Posta elettronica database. Se quando si imposta l'opzione su `0` l'applicazione è in esecuzione, continuerà a essere eseguita e a inviare la posta fino a quando non rimane inattiva per il tempo configurato nell'opzione `DatabaseMailExeMinimumLifeTime`.  
  
## <a name="examples"></a>Esempi
 Nel codice di esempio seguente vengono abilitate le stored procedure estese di Posta elettronica database.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  

Nel codice di esempio seguente vengono abilitate le stored procedure estese di Posta elettronica database, se non sono ancora abilitate.

```sql
IF EXISTS (
    SELECT 1 FROM sys.configurations 
    WHERE NAME = 'Database Mail XPs' AND VALUE = 0)
BEGIN
  PRINT 'Enabling Database Mail XPs'
  EXEC sp_configure 'show advanced options', 1;  
  RECONFIGURE
  EXEC sp_configure 'Database Mail XPs', 1;  
  RECONFIGURE  
END
```

## <a name="see-also"></a>Vedere anche
[Posta elettronica database](../../relational-databases/database-mail/database-mail.md)  
