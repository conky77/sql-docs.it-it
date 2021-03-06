---
title: Note sulla versione di SQL Server 2019 in Linux
description: Questo articolo contiene le note sulla versione e le funzionalità supportate per SQL Server 2019 in esecuzione in Linux. Sono incluse le note sulla versione per la versione più recente e per diverse versioni precedenti.
author: VanMSFT
ms.author: vanto
ms.date: 02/13/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 95289a3c4ad263e2c3ef063e54984a4481cf6109
ms.sourcegitcommit: 49082f9b6b3bc8aaf9ea3f8557f40c9f1b6f3b0b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77256784"
---
# <a name="release-notes-for-sql-server-2019-on-linux"></a>Note sulla versione di SQL Server 2019 in Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Le note sulla versione seguenti si applicano a SQL Server 2019 in esecuzione in Linux. Questo articolo è suddiviso in sezioni corrispondenti a ogni versione. Ogni versione ha un collegamento a un articolo del supporto che descrive le modifiche CU, oltre ai collegamenti ai download dei pacchetti Linux.

> [!TIP]
> Per informazioni sulle nuove funzionalità di Linux in SQL Server 2019, vedere [Novità di SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

## <a name="supported-platforms"></a>Piattaforme supportate

| Piattaforma | File system | Guida all'installazione |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, 7.4, 7.5, 7.6 o 8 Server | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-red-hat.md) | 
| SUSE Linux Enterprise Server v12 SP2, SP3 o SP4 | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS o EXT4 | [Guida all'installazione](quickstart-install-connect-ubuntu.md) | 
| Docker Engine 1.8+ in Windows, Mac o Linux | N/D | [Guida all'installazione](quickstart-install-connect-docker.md) | 

> [!TIP]
> Per altre informazioni, vedere i [requisiti di sistema](sql-server-linux-setup.md#system) per SQL Server in Linux. Per i criteri di supporto tecnico più recenti per SQL Server 2017, vedere [Criteri di supporto tecnico per Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Strumenti

La maggior parte degli strumenti client esistenti per SQL Server può essere facilmente usata per SQL Server in esecuzione in Linux. Per usare in modo efficiente alcuni strumenti in Linux, potrebbe essere richiesta una versione specifica. Per un elenco completo di strumenti di SQL Server, vedere [Strumenti e utilità SQL per SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Cronologia delle versioni

La tabella seguente elenca la cronologia delle versioni di SQL Server 2019.

| Versione                   | Versione       | Data di rilascio |
|---------------------------|---------------|--------------|
| [CU2](#cu2)               | 15.0.4013.40  | 2020-02-13   |
| [CU1](#cu1)               | 15.0.4003.23  | 07 gennaio 2020   |
| [GA](#ga)                 | 15.0.2000.5   | 4 novembre 2019   |
| [Release Candidate](#rc)  | 15.0.1900.25  | 21 agosto 2019   |

## <a id="cuinstall"></a> Come installare gli aggiornamenti

Se è stato configurato il repository di aggiornamenti cumulativi (mssql-server-2019), quando si eseguono nuove installazioni si otterrà l'aggiornamento cumulativo più recente dei pacchetti di SQL Server. Se sono necessarie immagini del contenitore Docker, vedere le immagini ufficiali per [Microsoft SQL Server in Linux per il motore Docker](https://hub.docker.com/r/microsoft/mssql-server/). Per altre informazioni sulla configurazione del repository, vedere [Configurare i repository per SQL Server in Linux](sql-server-linux-change-repo.md).

Se si aggiornano pacchetti di SQL Server esistenti, eseguire il comando di aggiornamento appropriato per ogni pacchetto per ottenere l'aggiornamento cumulativo più recente. Per istruzioni dettagliate sull'aggiornamento per ogni pacchetto, vedere le guide all'installazione seguenti:

- [Installare il pacchetto di SQL Server](sql-server-linux-setup.md#upgrade)
- [Installare il pacchetto di ricerca full-text](sql-server-linux-setup-full-text-search.md)
- [Installare SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Installare il supporto per R e Python per Machine Learning Services di SQL Server 2019 in Linux](sql-server-linux-setup-machine-learning.md)
- [Installare il pacchetto PolyBase](../relational-databases/polybase/polybase-linux-setup.md)
- [Abilitare SQL Server Agent](sql-server-linux-setup-sql-agent.md)

## <a id="cu2"></a> CU2 (febbraio 2020)

Questa è la versione Cumulative Update 2 (CU2) di SQL Server 2019 (15.x). La versione del motore di database di SQL Server per questa versione è 15.0.4013.40. Per informazioni sulle correzioni e sui miglioramenti, vedere <https://support.microsoft.com/help/4536075>

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni dei pacchetti manuali o offline, è possibile scaricare i pacchetti RPM e Debian con le informazioni riportate nella tabella seguente:

> [!NOTE]
> A partire da CU1, i collegamenti per l'installazione offline dei pacchetti per Red Hat indirizzeranno ai pacchetti RHEL 8. Per scaricare i pacchetti RHEL 7, fare riferimento al percorso di download <https://packages.microsoft.com/rhel/7/mssql-server-2019/>

| Pacchetto | Versione pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 15.0.4013.40-8 | [Pacchetto RPM del motore](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM a disponibilità elevata](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM di estendibilità](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM di estendibilità Java](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4013.40-8.x86_64.rpm)|
| Pacchetto SLES RPM | 15.0.4013.40-8 | [Pacchetto RPM del motore mssql-server](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM a disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM di estendibilità](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM di estendibilità Java](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4013.40-8.x86_64.rpm)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4013.40-8.x86_64.rpm)|
| Pacchetto Ubuntu 16.04 Debian | 15.0.4013.40-8 | [Pacchetto Debian del motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4013.40-8_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4013.40-8_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4013.40-8_amd64.deb)</br>[Pacchetto Debian di estendibilità](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4013.40-8_amd64.deb)</br>[Pacchetto Debian di estendibilità Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4013.40-8_amd64.deb)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4013.40-8_amd64.deb)|

## <a id="cu1"></a> CU1 (gennaio 2020)

Questa è la versione Cumulative Update 1 (CU1) di SQL Server 2019 (15.x). La versione del motore di database di SQL Server per questa versione è 15.0.4003.23. Per informazioni sulle correzioni e sui miglioramenti apportati in questa versione, vedere <https://support.microsoft.com/en-us/help/4527376>

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni dei pacchetti manuali o offline, è possibile scaricare i pacchetti RPM e Debian con le informazioni riportate nella tabella seguente:

> [!NOTE]
> A partire da CU1, i collegamenti per l'installazione offline dei pacchetti per Red Hat indirizzeranno ai pacchetti RHEL 8. Per scaricare i pacchetti RHEL 7, fare riferimento al percorso di download <https://packages.microsoft.com/rhel/7/mssql-server-2019/>

| Pacchetto | Versione pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 15.0.4003.23-3 | [Pacchetto RPM del motore](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM a disponibilità elevata](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-ha-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-fts-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM di estendibilità](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM di estendibilità Java](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-extensibility-java-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/rhel/8/mssql-server-2019/mssql-server-polybase-15.0.4003.23-3.x86_64.rpm)|
| Pacchetto SLES RPM | 15.0.4003.23-3 | [Pacchetto RPM del motore mssql-server](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM a disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM di estendibilità](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM di estendibilità Java](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.4003.23-3.x86_64.rpm)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.4003.23-3.x86_64.rpm)|
| Pacchetto Ubuntu 16.04 Debian | 15.0.4003.23-3 | [Pacchetto Debian del motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.4003.23-3_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.4003.23-3_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.4003.23-3_amd64.deb)</br>[Pacchetto Debian di estendibilità](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.4003.23-3_amd64.deb)</br>[Pacchetto Debian di estendibilità Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.4003.23-3_amd64.deb)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.4003.23-3_amd64.deb)|

## <a id="ga"></a> GA (novembre 2019)

Questa è la versione disponibile a livello generale (GA, General Availability) di SQL Server 2019 (15.x). La versione del motore di database di SQL Server per questa versione è 15.0.2000.5.

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni dei pacchetti manuali o offline, è possibile scaricare i pacchetti RPM e Debian con le informazioni riportate nella tabella seguente:

| Pacchetto | Versione pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 15.0.2000.5-5 | [Pacchetto RPM del motore](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM a disponibilità elevata](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-ha-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-fts-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM di estendibilità](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-extensibility-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM di estendibilità Java](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-extensibility-java-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-2019/mssql-server-polybase-15.0.2000.5-5.x86_64.rpm)|
| Pacchetto SLES RPM | 15.0.2000.5-5 | [Pacchetto RPM del motore mssql-server](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM a disponibilità elevata](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-ha-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-fts-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM di estendibilità](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM di estendibilità Java](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-extensibility-java-15.0.2000.5-5.x86_64.rpm)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-2019/mssql-server-polybase-15.0.2000.5-5.x86_64.rpm)|
| Pacchetto Ubuntu 16.04 Debian | 15.0.2000.5-5 | [Pacchetto Debian del motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server/mssql-server_15.0.2000.5-5_amd64.deb)</br>[Pacchetto Debian a disponibilità elevata](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.2000.5-5_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.2000.5-5_amd64.deb)</br>[Pacchetto Debian di estendibilità](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.2000.5-5_amd64.deb)</br>[Pacchetto Debian di estendibilità Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.2000.5-5_amd64.deb)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2019/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.2000.5-5_amd64.deb)|

## <a id="rc"></a> Release Candidate (agosto 2019)

Le sezioni seguenti elencano i percorsi dei pacchetti e i problemi noti per la versione finale candidata. Per altre informazioni sulle nuove funzionalità per Linux in SQL Server 2019, vedere [Novità di SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Dettagli del pacchetto

Per le installazioni dei pacchetti manuali o offline, è possibile scaricare i pacchetti RPM e Debian con le informazioni riportate nella tabella seguente:

| Pacchetto | Versione pacchetto | Download |
|-----|-----|-----|
| Pacchetto Red Hat RPM | 15.0.1900.25-1 | [Pacchetto RPM del motore](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1900.25-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1900.25-1.x86_64.rpm)</br>[Pacchetto RPM di estendibilità](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1900.25-1.x86_64.rpm)</br>[Pacchetto RPM di estendibilità Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1900.25-1.x86_64.rpm)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1900.25-1.x86_64.rpm)|
| Pacchetto SLES RPM | 15.0.1900.25-1 | [Pacchetto RPM del motore mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1900.25-1.x86_64.rpm)</br>[Pacchetto RPM di ricerca full-text](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1900.25-1.x86_64.rpm)</br>[Pacchetto RPM di estendibilità](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1900.25-1.x86_64.rpm)</br>[Pacchetto RPM di estendibilità Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1900.25-1.x86_64.rpm)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1900.25-1.x86_64.rpm)|
| Pacchetto Ubuntu 16.04 Debian | 15.0.1900.25-1 | [Pacchetto Debian del motore](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1900.25-1_amd64.deb)</br>[Pacchetto Debian di ricerca full-text](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1900.25-1_amd64.deb)</br>[Pacchetto Debian di estendibilità](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1900.25-1_amd64.deb)</br>[Pacchetto Debian di estendibilità Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1900.25-1_amd64.deb)</br>[Pacchetto RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1900.25-1_amd64.deb)|

## <a name="known-issues"></a>Problemi noti

Le sezioni seguenti descrivono i problemi noti della versione GA (General Availability) di SQL Server 2019 (15.x) in Linux.

### <a name="general"></a>Generale

- La lunghezza del nome host in cui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è installato non deve superare i 15 caratteri. 

    - **Soluzione**: sostituire il nome in /etc/hostname con uno di 15 caratteri o meno.

- Mettendo manualmente indietro l'ora di sistema, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] smetterà di aggiornare l'ora del sistema interno di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

    - **Soluzione**: Riavviare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

- Sono supportate solo le installazioni a istanza singola.

    - **Soluzione**: Se si vuole avere più di un'istanza in un determinato host, è consigliabile usare le macchine virtuali o i contenitori Docker. 

- Gestione configurazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non riesce a connettersi a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux.

- La lingua predefinita dell'account di accesso **sa** è l'inglese.

    - **Soluzione**: Cambiare la lingua dell'account di accesso **sa** con l'istruzione **ALTER LOGIN**.

- Il provider OLEDB registra l'avviso seguente: `Failed to verify the Authenticode signature of 'C:\binn\msoledbsql.dll'. Signature verification of SQL Server DLLs will be skipped. Genuine copies of SQL Server are signed. Failure to verify the Authenticode signature might indicate that this is not an authentic release of SQL Server. Install a genuine copy of SQL Server or contact customer support.`

   - **Soluzione**: Non è richiesta alcuna azione. Il provider OLEDB viene firmato con SHA256. Il motore di database di SQL Server non convalida correttamente il file .dll firmato.

### <a name="databases"></a>Database

- Non è possibile spostare il database master con l'utilità mssql-conf. È possibile spostare altri database di sistema con mssql-conf.

- Quando si ripristina un database di cui è stato eseguito un backup in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Windows, è necessario usare la clausola **WITH MOVE** nell'istruzione Transact-SQL.

- Alcuni algoritmi (suite di crittografia) per Transport Layer Security (TLS) non funzionano correttamente con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux. Ne derivano errori di connessione quando si prova a connettersi a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], oltre a problemi a stabilire le connessioni tra repliche nei gruppi di disponibilità elevata.

   - **Soluzione**: modificare lo script di configurazione **mssql.conf** per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux per disabilitare le suite di crittografia problematiche, seguendo questa procedura:

      1. Aggiungere il codice seguente a /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Riavviare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con il comando seguente.

      ```bash
      sudo systemctl restart mssql-server
      ```

- I database di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] in Windows che usano OLTP in memoria non possono essere ripristinati in SQL Server 2019 (15.x) in Linux. Per ripristinare un database di [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] che usa OLTP in memoria, aggiornare i database a [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], SQL Server 2017 o SQL Server 2019 in Windows prima di spostarli in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux tramite backup/ripristino o scollegamento/collegamento.

- L'autorizzazione utente **AMMINISTRAZIONE OPERAZIONI BULK** per il momento non è supportata in Linux.

### <a name="networking"></a>Rete

Le funzionalità che coinvolgono le connessioni TCP in uscita dal processo sqlservr, ad esempio i server collegati o i gruppi di disponibilità, potrebbero non funzionare se vengono soddisfatte entrambe le condizioni seguenti:

1. Il server di destinazione è specificato come nome host e non come indirizzo IP.

1. L'istanza di origine ha IPv6 disabilitato nel kernel. Per verificare se il sistema ha IPv6 abilitato nel kernel, è necessario che vengano superati tutti i test seguenti:

   - `cat /proc/cmdline` visualizzerà la riga di comando di avvio del kernel corrente. L'output non deve contenere `ipv6.disable=1`.
   - La directory /proc/sys/net/ipv6/ deve esistere.
   - Un programma C che chiama `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` deve avere esito positivo. Syscall deve restituire fd != -1 e non deve verificarsi l'errore EAFNOSUPPORT.

L'errore esatto dipende dalla funzionalità. Per i server collegati, viene presentato come errore di timeout di accesso. Per i gruppi di disponibilità, il DDL `ALTER AVAILABILITY GROUP JOIN` nel database secondario avrà esito negativo dopo 5 minuti con un errore di timeout della configurazione del download.

Per ovviare al problema, effettuare una delle seguenti operazioni:

1. Usare gli IP invece dei nomi host per specificare la destinazione della connessione TCP.

1. Abilitare IPv6 nel kernel rimuovendo `ipv6.disable=1` dalla riga di comando di avvio. La modalità di esecuzione di questa operazione dipende dalla distribuzione di Linux e dal bootloader, ad esempio grub. Se si vuole disabilitare IPv6, è comunque possibile farlo impostando `net.ipv6.conf.all.disable_ipv6 = 1` nella configurazione `sysctl` (ad esempio, `/etc/sysctl.conf`). Questa operazione impedirà comunque alla scheda di rete del sistema di ottenere un indirizzo IPv6, ma consentirà di usare le funzionalità di sqlservr.

#### <a name="network-file-system-nfs"></a>File system di rete (NFS)
Se si usano condivisioni di rete **NFS (Network File System, file system di rete)** nell'ambiente di produzione, tenere presenti i requisiti di supporto seguenti:

- Usare NFS versione **4.2 o successiva**. Le versioni precedenti di NFS non supportano le funzionalità necessarie, ad esempio `fallocate` e la creazione di file sparse, comuni ai file system moderni.
- Individuare solo le directory **/var/opt/mssql** nel montaggio NFS. Gli altri file, ad esempio i file binari di sistema di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], non sono supportati.
- Assicurarsi che i client NFS usino l'opzione `nolock` per il montaggio della condivisione remota.

### <a name="localization"></a>Localizzazione

- Se le impostazioni locali non sono in inglese (en_us) durante l'installazione, è necessario usare la codifica UTF-8 nella sessione/terminale Bash. Se si usa la codifica ASCII, potrebbe essere visualizzato un errore simile al seguente:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Se non è possibile usare la codifica UTF-8, eseguire il programma di installazione usando la variabile di ambiente MSSQL_LCID per specificare la lingua scelta.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Quando si eseguono la configurazione di mssql-conf e un'installazione non in inglese di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], vengono visualizzati caratteri estesi non corretti dopo il testo "Configurazione di SQL Server..." localizzato. Invece, per le installazioni non basate sull'alfabeto latino, la frase potrebbe mancare completamente. La frase mancante dovrebbe corrispondere alla stringa localizzata seguente: "Il PID di licenze è stato elaborato. La nuova edizione è [edizione \<Nome\>]". La stringa viene visualizzata solo a scopo informativo. Il problema verrà risolto nel successivo aggiornamento cumulativo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per tutte le lingue. Il problema non influisce in alcun modo sull'installazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

#### <a name="full-text-search"></a>Ricerca full-text

- Non tutti i filtri sono disponibili con questa versione, inclusi i filtri per i documenti di Office. Per un elenco di filtri supportati, vedere [Installare la ricerca full-text di SQL Server in Linux](sql-server-linux-setup-full-text-search.md#filters).

### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- In questa versione il pacchetto **mssql-server-is** non è supportato in SUSE. È attualmente supportato in Ubuntu e in Red Hat Enterprise Linux (RHEL).

- Con [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in Linux CTP 2.1 Refresh e versioni successive, i pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] possono usare le connessioni ODBC in Linux. Questa funzionalità è stata testata con i driver ODBC di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e MySQL, ma è previsto che funzioni anche con i driver ODBC Unicode che osservano la specifica ODBC. In fase di progettazione è possibile specificare un DSN o una stringa di connessione per la connessione ai dati ODBC. È anche possibile usare l'autenticazione di Windows. Per altre informazioni, vedere il [post di blog che annuncia il supporto ODBC in Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Le funzionalità seguenti non sono supportate in questa versione quando si eseguono pacchetti SSIS in Linux:
  - Database del catalogo di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]
  - Esecuzione pianificata dei pacchetti tramite SQL Agent
  - Autenticazione di Windows
  - Componenti di terze parti
  - Change Data Capture (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Scale Out
  - Feature Pack di Azure per SSIS
  - Supporto di Hadoop e HDFS
  - Microsoft Connector for SAP BW

Per un elenco di componenti SSIS predefiniti non attualmente supportati oppure supportati con limitazioni, vedere [Limitazioni e problemi noti per SSIS in Linux](sql-server-linux-ssis-known-issues.md#components).

Per altre informazioni su SSIS in Linux, vedere gli articoli seguenti:
-   [Post di blog che annuncia il supporto SSIS per Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installare SQL Server Integration Services (SSIS) in Linux](sql-server-linux-setup-ssis.md)
-   [Estrarre, trasformare e caricare i dati in Linux con SSIS](sql-server-linux-migrate-ssis.md)

### <a id="ssms"></a> SQL Server Management Studio (SSMS)

Le limitazioni seguenti si applicano a [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] in Windows connesso a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in Linux.

- I piani di manutenzione non sono supportati.

- Il data warehouse di gestione e l'agente di raccolta dati in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] non sono supportati. 

- I componenti dell'interfaccia utente di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] con le opzioni Autenticazione di Windows o Registro eventi di Windows non funzionano con Linux. È comunque possibile usare queste funzionalità con altre opzioni, ad esempio gli account di accesso SQL. 

- Non è possibile modificare il numero di file di log da conservare.

## <a name="next-steps"></a>Passaggi successivi

Per iniziare, vedere gli argomenti di avvio rapido seguenti:

- [Eseguire l'installazione in Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Eseguire l'installazione in SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Eseguire l'installazione in Ubuntu](quickstart-install-connect-ubuntu.md)
- [Esecuzione in Docker](quickstart-install-connect-ubuntu.md)
- [Eseguire il provisioning di una macchina virtuale SQL in Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Esecuzione e connessione - Cloud](quickstart-install-connect-clouds.md)

Per le risposte alle domande frequenti, vedere [Domande frequenti su SQL Server in Linux](sql-server-linux-faq.md).
