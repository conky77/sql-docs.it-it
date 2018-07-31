---
title: Metodi del servizio Web ReportServer | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- XML Web service [Reporting Services], features
- Web service [Reporting Services], features
- Report Server Web service, features
- XML Web service [Reporting Services], methods
ms.assetid: ce5afa27-e90c-44a7-b204-098a065b3665
caps.latest.revision: 48
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c6a5bbcbc994a3f5cc7e62a3fa80048505f88e26
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37168254"
---
# <a name="report-server-web-service-methods"></a>Metodi del servizio Web ReportServer
  I servizi Web ReportServer includono diverse categorie di metodi basate sulle caratteristiche dei componenti. Questi metodi vengono forniti tramite diversi endpoint del servizio Web (tre per la gestione e uno per l'esecuzione dei report) esposti come membri delle classi <xref:ReportService2010.ReportingService2010> e <xref:ReportExecution2005.ReportExecutionService>. Queste classi possono essere generate tramite uno strumento della classe proxy, ad esempio wsdl.exe incluso in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK. Per altre informazioni sui servizi Web ReportServer e [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], vedere [Compilazione di applicazioni tramite servizio Web e .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md).  
  
## <a name="endpoints-and-methods"></a>Endpoint e metodi  
 Nella tabella seguente vengono elencati gli endpoint del servizio Web ReportServer e le categorie di metodi forniti dall'endpoint <xref:ReportService2010.ReportingService2010>. Per altre informazioni sui metodi disponibili in altri endpoint, vedere [Riferimento tecnico &#40;SSRS&#41;](../../technical-reference-ssrs.md).  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Endpoint del servizio Web ReportServer](report-server-web-service-endpoints.md)|Descrive gli endpoint di gestione ed esecuzione del servizio Web ReportServer.|  
|[Metodi di gestione dello spazio dei nomi del server di report](report-server-namespace-management-methods.md)|Descrive i metodi che è possibile utilizzare per gestire il database del server di report. In particolare, è possibile gestire le cartelle e le risorse e impostare le proprietà dell'elemento.|  
|[Metodi di autorizzazione](authorization-methods.md)|Descrive i metodi che è possibile utilizzare per gestire attività, ruoli e criteri.|  
|[Origini dati e metodi di connessione](data-sources-and-connection-methods.md)|Descrive i metodi che è possibile utilizzare per impostare e gestire la connessione all'origine dati e le informazioni sulle credenziali per i report.|  
|[Metodi per i parametri dei report](report-parameters-methods.md)|Descrive i metodi che è possibile utilizzare per impostare e recuperare parametri per i report.|  
|[Metodi per i modelli](../report-server-web-service.md)|Descrive i metodi che è possibile utilizzare per gestire modelli.|  
|[Metodi di rendering e di esecuzione](rendering-and-execution-methods.md)|Descrive i metodi che è possibile utilizzare per gestire l'esecuzione, il rendering e la memorizzazione nella cache dei report.|  
|[Metodi relativi alla cronologia dei report](report-history-methods.md)|Descrive i metodi che è possibile utilizzare per creare e gestire gli snapshot della cronologia dei report.|  
|[Metodi di pianificazione](scheduling-methods.md)|Descrive i metodi che è possibile utilizzare per creare e gestire pianificazioni condivise e piani di aggiornamento della cache utilizzate dal server di report.|  
|[Metodi di sottoscrizione e recapito](subscription-and-delivery-methods.md)|Descrive i metodi che è possibile utilizzare per creare e gestire sottoscrizioni e recapito dei report.|  
|[Metodi dei report collegati](linked-reports-methods.md)|Descrive i metodi che è possibile utilizzare per creare e gestire i report collegati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso all'API SOAP](../accessing-the-soap-api.md)   
 [Compilazione di applicazioni tramite servizio Web e .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../report-server-web-service.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  