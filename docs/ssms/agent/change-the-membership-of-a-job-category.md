---
title: Modificare l'appartenenza a una categoria di processi
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: fc3bf68b927cfd162694cc78983a9a6155b25786
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "75254735"
---
# <a name="change-the-membership-of-a-job-category"></a>Modificare l'appartenenza a una categoria di processi
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In questo argomento viene descritto come modificare l'appartenenza della categoria di processi in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o SQL Server Management Objects.  
  
Le categorie consentono di organizzare i processi per semplificare le operazioni di raggruppamento e filtro. È possibile creare categorie di processi personalizzate. È inoltre possibile modificare l'appartenenza dei processi di Microsoft SQL Server Agent alle categorie del processo.  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Sicurezza  
Per informazioni dettagliate, vedere [Implementazione della sicurezza di SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Per modificare l'appartenenza a una categoria di processi  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera modificare una categoria di processi.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Processi** e selezionare **Gestione categorie processi**.  
  
4.  Nella finestra di dialogo **Gestione categorie processi**_nome_server_ selezionare la categoria di processi da modificare e fare clic su **Visualizza processi**.  
  
5.  Selezionare la casella di controllo **Mostra tutti i processi** .  
  
6.  Per aggiungere un processo alla categoria, selezionare nella griglia principale la casella di controllo della colonna **Seleziona** corrispondente al processo. Per rimuovere un processo dalla categoria, deselezionare la casella. Al termine, fare clic su **OK**.  
  
7.  Chiudere la finestra di dialogo **Gestione categorie processi**_nome_server_ .  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Per modificare l'appartenenza a una categoria di processi  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_update_job (Transact-SQL)](https://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623).  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per modificare l'appartenenza a una categoria di processi**  
  
Usare la classe **JobCategory** con un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell.  
  
