---
title: Ripristinare il database master (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], restoring
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6ce115a0df8ca77b37a78234247174ca9f2dd006
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68041475"
---
# <a name="restore-the-master-database-transact-sql"></a>Ripristinare il database master (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Questo argomento spiega come ripristinare il database **master** da un backup completo del database.  
  
### <a name="to-restore-the-master-database"></a>Per ripristinare il database master  
  
1.  Avviare l'istanza del server in modalità utente singolo.  
  
     Per informazioni su come specificare un parametro di avvio in modalità utente singolo ( **-m**), vedere [Configurare le opzioni di avvio del server &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).  
  
2.  Per ripristinare un backup completo del database **master**, usare l'istruzione [RESTORE DATABASE](../../t-sql/statements/restore-statements-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] seguente:  
  
     `RESTORE DATABASE master FROM`  *<backup_device>*  `WITH REPLACE`  
  
     L'opzione REPLACE indica a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di ripristinare il database specificato anche quando è già presente un database con lo stesso nome. Il database esistente, se presente, viene eliminato. In modalità utente singolo è consigliabile immettere l'istruzione RESTORE DATABASE nell' [utilità sqlcmd](../../tools/sqlcmd-utility.md). Per altre informazioni, vedere [Usare l'utilità sqlcmd](../../relational-databases/scripting/sqlcmd-use-the-utility.md).  
  
    > [!IMPORTANT]  
    >  Dopo il ripristino del database **master** , l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene arrestata e termina il processo di **sqlcmd** . Prima di riavviare l'istanza del server, rimuovere il parametro di avvio in modalità utente singolo. Per altre informazioni, vedere [Configurazione delle opzioni di avvio del server &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md).  
  
3.  Riavviare l'istanza del server e proseguire con gli altri passaggi di recupero, quali il ripristino di altri database, il collegamento dei database e la correzione delle mancate corrispondenze tra utenti.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene ripristinato il database `master` nell'istanza predefinita del server. In questo esempio si presuppone che l'istanza del server sia già in esecuzione in modalità utente singolo. Viene avviata l'utilità `sqlcmd` ed eseguita un'istruzione `RESTORE DATABASE` che ripristina un backup completo del database `master` da un dispositivo disco: `Z:\SQLServerBackups\master.bak`.  
  
> [!NOTE]  
>  Per un'istanza denominata, il comando **sqlcmd** deve specificare l'opzione **-S** _\<NomeComputer>_ \\ *\<NomeIstanza>* .  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristini di database completi &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [Ripristini di database completi &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Risolvere i problemi relativi agli utenti isolati &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [Ricompilare database di sistema](../../relational-databases/databases/rebuild-system-databases.md)   
 [Opzioni di avvio del servizio del motore di database](../../database-engine/configure-windows/database-engine-service-startup-options.md)   
 [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
 [Backup e ripristino di database di sistema &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [Avvio di SQL Server in modalità utente singolo](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  
