---
title: Sincronizzare gli orologi dei server di destinazione
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7fa715d0df6c94630564ede8a162a940542d7510
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "75257904"
---
# <a name="synchronize-target-server-clocks"></a>Sincronizzare gli orologi dei server di destinazione

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In questo argomento viene descritto come sincronizzare gli orologi dei server di destinazione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] con l'orologio del server master tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. La sincronizzazione di questi orologi di sistema supporta le pianificazioni dei processi.  

## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Sicurezza  
  
#### <a name="Permissions"></a>Autorizzazioni  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-synchronize-target-server-clocks"></a>Per sincronizzare gli orologi dei server di destinazione  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server di cui si desidera sincronizzare gli orologi del server di destinazione con l'orologio del server master.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, scegliere **Amministrazione multiserver**e selezionare **Gestione server di destinazione**.  
  
3.  Nella finestra di dialogo **Gestione server di destinazione** , fare clic su **Invia istruzioni**.  
  
4.  Nell'elenco **Tipo istruzione** selezionare **Sincronizza orologi**.  
  
5.  In **Destinatari**eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Tutti i server di destinazione** per sincronizzare gli orologi di tutti i server di destinazione con l'orologio del server master.  
  
    -   Fare clic su **Solo i server di destinazione** seguenti per sincronizzare gli orologi di alcuni server e quindi selezionare ogni server di destinazione di cui si desidera sincronizzare l'orologio con quello del server master.  
  
6.  Al termine, fare clic su **OK**.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-synchronize-target-server-clocks"></a>Per sincronizzare gli orologi dei server di destinazione  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_resync_targetserver (Transact-SQL)](https://msdn.microsoft.com/40e44df7-d3e3-44ee-b149-08aba629a21f).  
  
