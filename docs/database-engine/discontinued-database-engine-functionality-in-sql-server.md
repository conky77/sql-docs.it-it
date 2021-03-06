---
title: Funzionalità del motore di database non più disponibili | Microsoft Docs
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- SSL
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>= sql-server-linux-2017  || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: db10b57b5eda73cb2bb2105f4f99fb6e5cbed733
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "75258124"
---
# <a name="discontinued-database-engine-functionality-in-sql-server"></a>Funzionalità del motore di database sospese in SQL Server
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

  In questo argomento vengono descritte le funzionalità di [!INCLUDE[ssDE](../includes/ssde-md.md)] che non sono più disponibili in [!INCLUDE[ssCurrent](../includes/ssnoversion-md.md)].  

## <a name="discontinued-features-in-includesssqlv15includessssqlv15-mdmd"></a>Funzionalità sospese in [!INCLUDE[ssSQLv15](../includes/sssqlv15-md.md)]  

- Le seguenti opzioni di configurazione in ambito database sono sospese:

  - `DISABLE_BATCH_MODE_ADAPTIVE_JOIN`
  - `DISABLE_BATCH_MODE_MEMORY_GRANT_FEEDBACK`
  - `DISABLE_INTERLEAVED_EXECUTION_TVF`

Per le opzioni di configurazione correnti, vedere [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

>[!NOTE]
>Nessuna funzionalità è stata sospesa in [!INCLUDE[ssSQLv14](../includes/sssqlv14-md.md)].

## <a name="discontinued-features-in-includesssql15includessssql15-mdmd"></a>Funzionalità sospese in [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]

- [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] è un'applicazione a 64 bit. L'installazione a 32 bit è stata sospesa, ma alcuni elementi vengono eseguiti come componenti a 32 bit.  

- Il livello di compatibilità 90 non è più disponibile. Per altre informazioni, vedere [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  

- Il sottosistema ActiveX non è più disponibile. Usare la linea di comando o gli script di PowerShell.

- Parametri di avvio **-h** e **-g**. Per altre informazioni, vedere [Opzioni di avvio del servizio del motore di database](https://docs.microsoft.com/sql/database-engine/configure-windows/database-engine-service-startup-options?view=sql-server-2014).

- La crittografia SSL (Secure Sockets Layer) non è più disponibile. Usare in alternativa Transport Layer Security (TLS). Per altre informazioni, vedere [Abilitazione di connessioni crittografate al Motore di database](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).

## <a name="previous-versions"></a>Versioni precedenti

- [Funzionalità del Motore di database non più utilizzate in SQL Server 2014](https://docs.microsoft.com/sql/database-engine/discontinued-database-engine-functionality-in-sql-server-2016?view=sql-server-2014)

### <a name="see-also"></a>Vedere anche

- [Funzionalità del motore di database deprecate in SQL Server 2019](deprecated-database-engine-features-in-sql-server-version-15.md)
- [Funzionalità del motore di database deprecate in SQL Server 2017](deprecated-database-engine-features-in-sql-server-2017.md)
- [Funzionalità del motore di database deprecate in SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)
- [Modifiche che causano interruzioni apportate alle funzionalità del motore di database in SQL Server 2019](breaking-changes-to-database-engine-features-in-sql-server-version-15.md)
- [Modifiche che causano interruzioni apportate alle funzionalità del motore di database in SQL Server 2017](breaking-changes-to-database-engine-features-in-sql-server-2017.md)
- [Modifiche che causano interruzioni apportate alle funzionalità del motore di database in SQL Server 2016](breaking-changes-to-database-engine-features-in-sql-server-2016.md)
- [Funzionalità deprecate nella replica di SQL Server](../relational-databases/replication/deprecated-features-in-sql-server-replication.md)