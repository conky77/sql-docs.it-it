---
title: Oggetto General Statistics di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:General Statistics
- General Statistics object
ms.assetid: c738e549-d7e7-4211-9ec3-064ac140af7c
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 5d835a317f2968775f0cc94df19866c0d083d69d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68093519"
---
# <a name="sql-server-general-statistics-object"></a>Oggetto Statistiche generali di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'oggetto **SQLServer:General Statistics** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include contatori che consentono di monitorare l'attività generale del server, ad esempio il numero di connessioni correnti e il numero di utenti al secondo che si connettono e disconnettono dai computer che eseguono un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo tipo di monitoraggio è particolarmente utile nei sistemi di elaborazione delle transazioni online (OLTP) di grandi dimensioni in cui numerosi client si connettono e disconnettono da computer che eseguono un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Nella tabella seguente vengono descritti i contatori dell'oggetto **General Statistics** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Contatori Statistiche generali di SQL Server|Descrizione|  
|--------------------------------------------|-----------------|  
|**Tabelle temporanee attive**|Numero di tabelle temporanee/variabili di tabella in uso|  
|**Reimpostazioni della connessione/sec**|Numero totale di accessi avviato dal pool di connessioni.|  
|**Eliminazione posticipata notifiche eventi**|Numero di notifiche degli eventi in attesa di essere eliminate da un thread di sistema.|  
|**Richieste autenticate HTTP**|Numero di richieste autenticate HTTP avviate al secondo.|  
|**Connessioni logiche**|Numero di connessioni logiche al sistema.<br /><br /> Lo scopo principale delle connessioni logiche è di soddisfare più richieste MARS (Multiple Active Result Set). Per le richieste MARS, ogni volta che un'applicazione stabilisce una connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ci potrebbe essere più di una connessione logica che corrisponde a una connessione fisica.<br /><br /> Quando non viene utilizzato MARS, il rapporto tra connessioni fisiche e logiche è 1:1. Pertanto, ogni volta che un'applicazione stabilisce una connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le connessioni logiche aumenteranno di 1.|  
|**Accessi/sec**|Numero totale di accessi eseguiti al secondo. Non include connessioni dal pool.|  
|**Disconnessioni/sec**|Numero totale di operazioni di disconnessione avviate al secondo.|  
|**Deadlock MARS**|Numero di deadlock MARS rilevati.|  
|**Frequenza transazioni non atomiche**|Numero di transazioni non atomiche al secondo.|  
|**Processi bloccati**|Numero corrente di processi bloccati.|  
|**Richieste vuote SOAP**|Numero di richieste vuote SOAP avviate al secondo.|  
|**Chiamate di metodo SOAP**|Numero di chiamate di metodo SOAP avviate al secondo.|  
|**Richieste inizio sessione SOAP**|Numero di richieste di inizializzazione di sessione SOAP avviate al secondo.|  
|**Richieste termine sessione SOAP**|Numero di richieste di termine di sessione SOAP avviate al secondo.|  
|**Richieste SQL SOAP**|Numero di richieste SQL SOAP avviate al secondo.|  
|**Richieste WSDL SOAP**|Numero di richieste WSDL (Web Service Description Language) SOAP avviate al secondo.|  
|**Attese blocco provider I/O Traccia SQL**|Numero di attese di blocco del provider di I/O file al secondo.| 
|**Frequenza creazione tabelle temporanee**|Numero di tabelle temporanee/variabili di tabella create al secondo.|  
|**Tabelle temporanee da eliminare**|Numero di tabelle/variabili di tabella temporanee in attesa di essere eliminate dal thread di sistema di pulizia.|  
|**ID unità di recupero tempdb**|Numero di ID di unità di recupero tempdb duplicati generati.|
|**ID set di righe tempdb**|Numero di ID di set di righe tempdb duplicati generati.| 
|**Coda notifiche eventi di traccia**|Numero di istanze di notifiche degli eventi di traccia presenti nella coda interna in attesa dell'invio tramite Service Broker.|  
|**Transazioni**|Numero di transazioni integrate (tutte in combinazione: locali, DTC, associate).|  
|**Connessioni utente**|Numero di utenti attualmente connessi a SQL Server.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
