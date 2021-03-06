---
title: Impostazioni del sito di SharePoint per la Web part del Visualizzatore di report - SSRS | Microsoft Docs
ms.date: 11/15/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-sharepoint
ms.topic: conceptual
author: jt000
ms.author: jasontre
ms.openlocfilehash: 8eadb83c35f69dc2a1dba108e83df93bf614be3e
ms.sourcegitcommit: 49082f9b6b3bc8aaf9ea3f8557f40c9f1b6f3b0b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77256810"
---
# <a name="sharepoint-site-settings-for-the-report-viewer-web-part---reporting-services"></a>Impostazioni del sito di SharePoint per la Web part del Visualizzatore di report - Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)]  [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-and-later](../../includes/ssrs-appliesto-sharepoint-2013-and-later.md)] [!INCLUDE[ssrs-appliesto-not-sharepoint-online](../../includes/ssrs-appliesto-not-sharepoint-online.md)]

La Web part del Visualizzatore di report ha alcune impostazioni che possono essere configurate. Tali impostazioni possono essere abilitate e disabilitate dalla pagina delle impostazioni del sito di SharePoint da un amministratore del sito. Ogni sito ha le proprie impostazioni e che queste non saranno ripristinate dopo la reinstallazione della Web part del Visualizzatore di report.

## <a name="accessing-the-site-settings-page"></a>Accesso alla pagina delle impostazioni del sito

È possibile accedere alle impostazioni del sito con le modalità seguenti:

1. Nel sito di SharePoint selezionare l'icona dell'**ingranaggio** in alto a sinistra e selezionare **Impostazioni sito**.

    ![Impostazioni sito dall'icona dell'ingranaggio.](media/sharepoint-site-settings.png)

2. Fare clic su **Impostazioni della web part Visualizzatore di report** nel gruppo di impostazioni del sito **Reporting Services**.

    > [!NOTE]
    > È possibile accedere alle impostazioni del sito anche passando direttamente a `<site>/_layouts/15/ReportViewerWebPart/ReportViewerWebPartSettings.aspx`

## <a name="report-viewer-web-part-settings"></a>Impostazioni della web part del Visualizzatore di report

|Impostazione|Commenti|  
|-------------|--------------|  
|Raccolta dei dati sull'utilizzo|Consente l'invio a Microsoft delle informazioni sugli errori e sull'uso al fine di contribuire a migliorare i prodotti. Per informazioni sui criteri di raccolta dei dati di errore di Microsoft, vedere [Informativa sulla privacy di SQL Server](https://go.microsoft.com/fwlink/?LinkID=868444).|  
|Abilita i metadati di accessibilità per i report|Imposta le [informazioni sul dispositivo `AccessibleTablix`](../html-device-information-settings.md) per i report visualizzabili.| 
