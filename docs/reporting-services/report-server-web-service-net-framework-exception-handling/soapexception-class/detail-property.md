---
title: Proprietà Detail | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 087f7f6da8882f181c55a187438d4493ec5b1a9b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "62991564"
---
# <a name="detail-property"></a>Proprietà Detail
  La proprietà **Detail** della classe [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** ha la struttura XML seguente:  
  
## <a name="elements"></a>Elementi  
 **Detail**  
 Elemento di livello principale che contiene tutti gli altri elementi relativi ai dettagli dell'errore.  
  
 **ErrorCode**  
 Codice di errore specifico di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 **HttpStatus**  
 Codice di stato HTTP.  
  
 **Messaggio**  
 Messaggio di errore e codice di errore assegnati dal server di report.  
  
 **HelpLink**  
 URL di collegamento alla Guida che rimanda a un sito Web in cui è possibile trovare ulteriori informazioni sull'errore. Per altre informazioni, vedere [Elemento HelpLink](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).  
  
 **LinkID**  
 ID assegnato al collegamento.  
  
 **ProductName**  
 Nome del prodotto. Il valore predefinito è **Microsoft SQL Server Reporting Services**.  
  
 **ProductVersion**  
 Versione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. La lunghezza massima è di 15 caratteri. Il formato del numero di versione deve essere analogo a: 8.00.0xxx.00.  
  
 **ProductLocaleId**  
 ID delle impostazioni locali o della lingua della DLL INTL dell'applicazione (ad esempio, 0x41A).  
  
 **OperatingSystem**  
 Sistema operativo in cui è installato [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. I valori validi includono **0** per indicare una versione indipendente dal sistema operativo, **1** per [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)] e **16** per Windows XP.  
  
 **CountryLocaleId**  
 ID delle impostazioni locali o della lingua del sistema operativo. Il valore della versione francese di Windows è ad esempio 0x040c.  
  
 **MoreInformation**  
 Stringa XML contenente eccezioni nidificate che si sono verificate durante l'esecuzione del metodo.  
  
 **Origine**  
 Elemento figlio di **MoreInformation**. Indica l'origine dell'errore.  
  
 **Messaggio**  
 Elemento figlio di **MoreInformation**. Indica il messaggio di errore di un'eccezione nidificata. Questo elemento include gli attributi XML per **ErrorCode** e **HelpLink**.  
  
 **Avvisi**  
 Stringa XML contenente gli avvisi restituiti dall'elaborazione del report.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione alla gestione delle eccezioni in Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException di Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Uso della proprietà Detail per la gestione di errori specifici](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
