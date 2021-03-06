---
title: File di query collegamento (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 1ba0219a-6c40-41fa-aff9-8c8f41ef3220
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 11e875d5b171194c3ac8ba4ad33fad51cacacffe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482664"
---
# <a name="shortcut-query-files-mds-add-in-for-excel"></a>File di query collegamento (componente aggiuntivo MDS per Excel)
  Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]usare i file di query collegamento per connettersi rapidamente e caricare i dati usati di frequente. È possibile utilizzarli anche quando si desidera condividere dati MDS con gli altri utenti. Anziché salvare il foglio di lavoro e inviarlo tramite posta elettronica, è necessario salvare un file di query collegamento e inviarlo tramite posta elettronica. In tal modo si assicura la connessione al repository MDS per il mittente e il destinatario in modo da ottenere gli ultimi dati.  
  
 I file di query collegamento sono file XML che contengono informazioni su:  
  
-   La connessione al repository MDS.  
  
-   Il modello, la versione e l'entità.  
  
-   Qualsiasi filtro applicato quando è stato creato il collegamento.  
  
-   L'ordine da sinistra a destra delle colonne quando è stato creato il collegamento.  
  
 È possibile salvare questi file in un elenco e scegliere quello desiderato quando si apre il componente aggiuntivo. È possibile esportarli nel proprio computer o in un percorso condiviso o è possibile inviarli ad altri utenti.  
  
## <a name="queryopener-application"></a>Applicazione QueryOpener  
 Tutti gli utenti che installano [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] dispongono di un'applicazione, chiamata QueryOpener, installata. Questa applicazione è utilizzata per aprire i file di query collegamento in [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]. Se si fa doppio clic su un file di query collegamento, questa applicazione viene utilizzata automaticamente per aprire il file nel componente aggiuntivo.  
  
 Quando si apre un file di query collegamento con questa applicazione, viene richiesto di rendere la connessione "sicura", cioè si è sicuri del contenuto di questo percorso. Ogni volta che si contrassegna una connessione come sicura, viene aggiunta a un elenco. Se si desidera deselezionare questo elenco, aprire la finestra di dialogo **Impostazioni** e nella sezione **Server aggiunti a elenco attendibili** , fare clic su **Deseleziona tutto**.  
  
 Il percorso predefinito per l'applicazione è *unità*: \Programmi\microsoft SQL Server\120\Master Data Services\Excel Add-In\Microsoft.MasterDataServices.QueryOpener.exe.  
  
 Sono disponibili due modalità per aprire i file di query collegamento: è possibile importarli o fare doppio clic per aprirli automaticamente.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Salvare il contenuto del foglio di lavoro attivo come file di query collegamento.|[Salvare un file di query collegamento &#40;Componente aggiuntivo MDS per Excel&#41;](save-a-shortcut-query-file-mds-add-in-for-excel.md)|  
|Inviare tramite posta elettronica un file di query collegamento che rappresenta il contenuto del foglio di lavoro attivo.|[Inviare tramite posta elettronica un file di query collegamento &#40;Componente aggiuntivo MDS per Excel&#41;](email-a-shortcut-query-file-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Connessioni &#40;Componente aggiuntivo MDS per Excel&#41;](connections-mds-add-in-for-excel.md)  
  
-   [Componente aggiuntivo Master Data Services per Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
-   [&#40;di sicurezza Master Data Services&#41;](../security-master-data-services.md)  
  
  
