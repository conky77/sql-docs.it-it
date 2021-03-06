---
title: Introduzione
titleSuffix: SQL Server Big Data Clusters
description: Informazioni sulle risorse e sui passaggi necessari per la distribuzione di cluster Big Data di SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 02c3e6e217ea2918ab36829d6f0cceb4a6269e81
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "74190393"
---
# <a name="get-started-with-big-data-clusters-2019"></a>Introduzione ai [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Questo articolo offre una panoramica della distribuzione di [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md).

Per altri scenari di distribuzione, vedere:

- [Windows](../database-engine/install-windows/install-sql-server.md)
- [Linux](../linux/sql-server-linux-setup.md)
- [Contenitori Docker](../linux/sql-server-linux-configure-docker.md)

Questo articolo presenta i concetti principali e un quadro generale per la comprensione degli altri articoli sulla distribuzione inclusi in questa sezione. I passaggi di distribuzione specifici variano in base alla piattaforma scelta per il client e il server.

> [!TIP]
> Per ottenere rapidamente un ambiente in cui siano già distribuiti Kubernetes e un cluster Big Data e rendere più semplice l'apprendimento delle relative funzionalità, usare uno degli script di esempio indicati nella [sezione degli script](#scripts). Dopo la distribuzione, per gestire il cluster usare gli [strumenti client](#tools) nella sezione seguente.

Guardare questo video di 9 minuti per una panoramica della distribuzione di cluster Big Data:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Big-Data-Clusters-deployment-overview/player?WT.mc_id=dataexposed-c9-niner]


## <a id="tools"></a> Strumenti client

I cluster Big data richiedono un set specifico di strumenti client. Prima di distribuire un cluster Big Data in Kubernetes, è necessario installare gli strumenti seguenti:

| Strumento | Descrizione |
|---|---|
| **azdata** | Distribuisce e gestisce cluster Big Data. |
| **kubectl** | Crea e gestisce il cluster Kubernetes sottostante. |
| **Azure Data Studio** | Interfaccia grafica per l'uso del cluster Big Data. |
| **Estensione di SQL Server 2019** | Estensione di Azure Data Studio che abilita le funzionalità dei cluster Big Data. |

Per scenari diversi sono necessari altri strumenti. Ogni articolo descriverà gli strumenti necessari come prerequisiti per l'esecuzione di un'attività specifica. Per un elenco completo degli strumenti e dei collegamenti di installazione, vedere [Installare strumenti per Big Data di SQL Server 2019](deploy-big-data-tools.md).

## <a name="kubernetes"></a>Kubernetes

I cluster Big Data vengono distribuiti come serie di contenitori intercorrelati gestiti in [Kubernetes](https://kubernetes.io/docs/home). È possibile ospitare Kubernetes in diversi modi. Anche se esiste già un ambiente Kubernetes, è necessario esaminare i requisiti correlati per i cluster Big Data.

- **Servizio Azure Kubernetes**: il servizio Azure Kubernetes permette di distribuire un cluster Kubernetes gestito in Azure. È possibile gestire solo i nodi agente. Con il servizio Azure Kubernetes non è necessario effettuare il provisioning del proprio hardware per il cluster. È facile usare anche uno [script Python](quickstart-big-data-cluster-deploy.md) o un [notebook di distribuzione](deploy-notebooks.md) per creare il cluster del servizio Azure Kubernetes e distribuire il cluster Big Data in un unico passaggio. Per altre informazioni sulla configurazione del servizio Azure Kubernetes per la distribuzione di un cluster Big Data, vedere [Configurare il servizio Azure Kubernetes per distribuzioni di [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](deploy-on-aks.md).

- **Più computer**: è possibile distribuire Kubernetes anche in più computer Linux, che possono essere server fisici o macchine virtuali. È possibile usare lo strumento [kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) per creare il cluster Kubernetes. È possibile usare uno [script Bash](deployment-script-single-node-kubeadm.md) per automatizzare questo tipo di distribuzione. Questo metodo funziona correttamente se è già presente un'infrastruttura che si vuole usare per il cluster Big Data. Per altre informazioni sull'uso di distribuzioni **kubeadm** con cluster Big Data, vedere [Configurare Kubernetes in più computer per distribuzioni di [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](deploy-with-kubeadm.md).

## <a name="deploy-a-big-data-cluster"></a>Distribuire un cluster Big Data

Dopo aver configurato Kubernetes, è possibile distribuire un cluster Big Data con il comando `azdata bdc create`. Per la distribuzione è possibile adottare diversi approcci.

- Se si esegue la distribuzione in un ambiente di sviluppo e test, è possibile scegliere di usare una delle [configurazioni predefinite](deployment-guidance.md#deploy) fornite da **azdata**.

- Per personalizzare la distribuzione, è possibile creare e usare [file di configurazione della distribuzione](deployment-guidance.md#configfile) propri.

- Per un'installazione completamente automatica, è possibile passare tutte le altre impostazioni in variabili di ambiente. Per altre informazioni, vedere [Distribuzioni automatiche](deployment-guidance.md#unattended).


## <a id="scripts"></a> Script di distribuzione

Gli script di distribuzione permettono di distribuire cluster Kubernetes e Big Data in un unico passaggio. Spesso forniscono anche valori predefiniti per le impostazioni dei cluster Big Data. È possibile personalizzare qualsiasi script di distribuzione creando la propria versione, per configurare la distribuzione del cluster Big Data in modo diverso.

Attualmente sono disponibili gli script di distribuzione seguenti:

- [Script Python: distribuire un cluster Big Data nel servizio Azure Kubernetes](quickstart-big-data-cluster-deploy.md)
- [Script Bash: distribuire un cluster Big Data in un cluster kubeadm a nodo singolo](deployment-script-single-node-kubeadm.md)

## <a name="deployment-notebooks"></a>Notebook di distribuzione

È possibile distribuire un cluster Big Data anche eseguendo un notebook di Azure Data Studio. Per altre informazioni su come usare un notebook per la distribuzione nel servizio Azure Kubernetes, vedere l'articolo seguente:

- [Distribuire un cluster Big Data con notebook di Azure Data Studio](deploy-notebooks.md).

## <a name="next-steps"></a>Passaggi successivi

Dopo aver distribuito correttamente un cluster Big Data, [connettersi al cluster](connect-to-big-data-cluster.md) e valutare se [caricare dati di esempio](tutorial-load-sample-data.md) da usare con diverse procedure dettagliate.
