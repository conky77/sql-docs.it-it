---
title: Crittografia dei backup | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 334b95a8-6061-4fe0-9e34-b32c9f1706ce
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19a8597136f073d609c7a9cc77ce8e2b73c72004
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "71688296"
---
# <a name="backup-encryption"></a>Crittografia dei backup
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene fornita una panoramica delle opzioni di crittografia per i backup di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vengono illustrati i dettagli di utilizzo, i vantaggi e le procedure consigliate per eseguire la crittografia durante il backup.  

## <a name="Overview"></a> Panoramica  
 A partire da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], in SQL Server è possibile crittografare i dati durante la creazione di un backup. Specificando l'algoritmo di crittografia e il componente di crittografia (certificato o chiave asimmetrica) durante la creazione di un backup, è possibile creare un file di backup crittografato. Sono supportate tutte le destinazioni di archiviazione, in locale e Windows Azure. Inoltre, è possibile configurare le opzioni di crittografia per le operazioni del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] , una nuova funzionalità introdotta in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Per crittografare durante il backup, è necessario specificare un algoritmo di crittografia e un componente di crittografia per proteggere la chiave di crittografia. Di seguito sono riportate le opzioni di crittografia supportate:  
  
- **Algoritmo di crittografia:** gli algoritmi di crittografia supportati sono AES 128, AES 192, AES 256 e Triple DES  
  
- **Componente di crittografia:** certificato o chiave asimmetrica  
  
> [!CAUTION]  
> È molto importante eseguire il backup del certificato o della chiave asimmetrica e preferibilmente in un percorso diverso dal file di backup utilizzato per la crittografia. Senza il certificato o la chiave asimmetrica, non è possibile ripristinare il backup, rendendo il file di backup inutilizzabile.  
  
 **Ripristino del backup crittografato:** durante le operazioni di ripristino di SQL Server non è necessario specificare alcun parametro di crittografia. È necessario che la chiave asimmetrica o il certificato utilizzato per crittografare il file di backup sia disponibile nell'istanza in cui viene eseguito il ripristino. L'account utente che esegue il ripristino deve disporre delle autorizzazioni **VIEW DEFINITION** per il certificato o la chiave. Se si esegue il ripristino del backup crittografato in un'istanza diversa, è necessario assicurarsi che il certificato sia disponibile in tale istanza.  
  
 Se si esegue il ripristino di un backup da un database crittografato con TDE, è necessario che il certificato TDE sia disponibile nell'istanza in cui viene eseguito il ripristino.  
  
##  <a name="Benefits"></a> Vantaggi  
  
1. La crittografia dei backup dei database facilita la protezione dei dati: in SQL Server è possibile scegliere di crittografare i dati di backup durante la creazione di un backup.  
  
1. La crittografia può essere utilizzata anche per i database crittografati tramite TDE.  
  
1. La crittografia è supportata per i backup eseguiti dal [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)], assicurando una maggiore sicurezza per i backup esterni.  
  
1. Questa funzionalità supporta più algoritmi di crittografia fino ad AES a 256 bit, offrendo la possibilità di scegliere l'algoritmo più adatto alle specifiche esigenze.  
  
1. È possibile integrare le chiavi di crittografia con i provider EKM (Extended Key Management).  
 
##  <a name="Prerequisites"></a> Prerequisiti  
 Di seguito sono riportati i prerequisiti per crittografare un backup:  
  
1. **Creare una chiave master del database per il database master:** la chiave master del database è una chiave simmetrica utilizzata per proteggere le chiavi private dei certificati e le chiavi asimmetriche presenti nel database. Per altre informazioni, vedere [Chiavi di crittografia del database e di SQL Server &#40;Motore di database&#41;](../../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md).  
  
1. Creare un certificato o una chiave asimmetrica da utilizzare per la crittografia dei backup. Per altre informazioni sulla creazione di un certificato, vedere [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md). Per altre informazioni sulla creazione di una chiave asimmetrica, vedere [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md).  
  
    > [!IMPORTANT]  
    >  Sono supportate solo le chiavi asimmetriche che risiedono in un provider EKM (Extended Key Management).  
  
##  <a name="Restrictions"></a> Restrizioni  
 Di seguito sono riportate le restrizioni applicate alle opzioni di crittografia:  
  
- Se si utilizza la chiave asimmetrica per crittografare i dati di backup, sono supportate solo le chiavi asimmetriche che risiedono nel provider EKM.  
  
- SQL Server Express e SQL Server Web non supportano la crittografia durante il backup. È tuttavia supportato il ripristino da un backup crittografato in un'istanza di SQL Server Express o SQL Server Web.  
  
- Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è possibile leggere i backup crittografati.  
  
- L'opzione Accoda al set di backup esistente non è supportata per i backup crittografati.  

##  <a name="Permissions"></a> Autorizzazioni  

Per crittografare un backup o per eseguire il ripristino da un backup crittografato, usare l'autorizzazione **VIEW DEFINITION** per la chiave asimmetrica o il certificato usato per crittografare il backup del database.  
  
> [!NOTE]  
> L'accesso al certificato TDE non è necessario per eseguire il backup o il ripristino di un database protetto con TDE.  
  
## <a name="Methods"></a> Metodi di crittografia dei backup  
 Nelle sezioni seguenti viene fornita una breve introduzione ai passaggi per crittografare i dati durante il backup. Per una procedura dettagliata completa per la crittografia del backup con Transact-SQL, vedere [Creare un backup crittografato](../../relational-databases/backup-restore/create-an-encrypted-backup.md).  
  
### <a name="using-sql-server-management-studio"></a>Utilizzare SQL Server Management Studio  
 È possibile crittografare un backup durante la creazione del backup di un database in una delle finestre di dialogo seguenti:  
  
1. [Backup database &#40;pagina Opzioni di backup&#41;](../../relational-databases/backup-restore/back-up-database-backup-options-page.md) Nella pagina **Opzioni di backup** è possibile selezionare **Crittografia** e specificare l'algoritmo di crittografia e il certificato o la chiave asimmetrica da usare per la crittografia.  
  
1. [Utilizzo di Creazione guidata piano di manutenzione](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) Quando si seleziona un'attività di backup, nella scheda **Opzioni** della pagina **Definizione attività Backup database ()** è possibile selezionare **Crittografia backup**e specificare l'algoritmo di crittografia e il certificato o la chiave da usare per la crittografia.  
  
### <a name="using-transact-sql"></a>Uso di Transact-SQL  
 Di seguito è riportata un'istruzione T-SQL di esempio per crittografare il file di backup:  
  
```sql  
BACKUP DATABASE [MYTestDB]  
TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
WITH  
  COMPRESSION,  
  ENCRYPTION   
   (  
   ALGORITHM = AES_256,  
   SERVER CERTIFICATE = BackupEncryptCert  
   ),  
  STATS = 10  
GO  
```  
  
 Per la sintassi completa dell'istruzione Transact-SQL, vedere [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md).  
  
### <a name="using-powershell"></a>Utilizzo di PowerShell  
 Questo esempio illustra come creare le opzioni di crittografia, usate come valore di parametro nel cmdlet **Backup-SqlDatabase** per creare un backup crittografato.  
  
```powershell
$encryptionOption = New-SqlBackupEncryptionOption -Algorithm Aes256 -EncryptorType ServerCertificate -EncryptorName "BackupCert"  

Backup-SqlDatabase -ServerInstance . -Database "<myDatabase>" -BackupFile "<myDatabase>.bak" -CompressionOption On -EncryptionOption $encryptionOption  
```  
  
##  <a name="RecommendedPractices"></a> Procedure consigliate  
 Creare un backup del certificato e delle chiavi di crittografia in un percorso diverso dal computer locale in cui è installata l'istanza. Tenendo in considerazione gli scenari di ripristino di emergenza, è consigliabile archiviare un backup del certificato o della chiave in una posizione esterna. Non è possibile ripristinare un backup crittografato senza il certificato utilizzato per crittografarlo.  
  
 Per ripristinare un backup crittografato, è necessario che il certificato originale utilizzato durante la creazione del backup con l'identificazione digitale corrispondente sia disponibile nell'istanza in cui viene eseguito il ripristino. Pertanto, il certificato non deve essere rinnovato alla scadenza né modificato in alcun modo. Il rinnovo può comportare un aggiornamento del certificato con conseguente modifica dell'identificazione digitale, rendendo pertanto il certificato non valido per il file di backup. L'account che esegue il ripristino deve disporre delle autorizzazioni VIEW DEFINITION per la chiave asimmetrica o il certificato utilizzato per eseguire la crittografia durante il backup.  
  
 I backup del database del gruppo di disponibilità vengono in genere eseguiti nella replica di backup preferita.  Se si ripristina un backup in una replica diversa da dove è stato eseguito il backup, verificare che il certificato originale utilizzato per il backup sia disponibile nella replica a cui si esegue il ripristino.  
  
 Se per il database è abilitata la funzionalità TDE, scegliere certificati o chiavi asimmetriche diverse per crittografare il database e il backup in modo da aumentare il livello di sicurezza.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
|Argomento/Attività|Descrizione|  
|-----------------|-----------------|  
|[Creare un backup crittografato](../../relational-databases/backup-restore/create-an-encrypted-backup.md)|Vengono descritti i passaggi di base necessari per creare un backup crittografato|  
|[Extensible Key Management con l'insieme di credenziali delle chiavi di Azure &#40;SQL Server&#41;](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)|Fornisce un esempio di creazione di un backup crittografato protetto da chiavi nell'insieme di credenziali delle chiavi di Azure.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)  
