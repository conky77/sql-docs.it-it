---
title: Autorizzazioni necessarie per la connessione a SQL per il servizio CDC | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e7528545f2b7cd50e4b612372dc35e65dcc2324a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "71298643"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>Autorizzazioni necessarie per la connessione a SQL per il servizio CDC

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Per eseguire le attività, CDC Service Configuration Console richiede informazioni di connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In questo argomento vengono illustrate le informazioni che è possibile specificare nella finestra di dialogo Connect to SQL Server per l'impostazione della connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La finestra di dialogo Connect to SQL Server viene visualizzata quando necessario, ad esempio quando le informazioni di connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non sono disponibili o quando le informazioni sono presenti, ma la connessione non dispone delle autorizzazioni necessarie.  
  
 Nella tabella seguente vengono descritte le diverse attività per le quali è necessario disporre di una connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e le autorizzazioni necessarie relative all'utente o all'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Attività|Autorizzazioni minime|  
|----------|-------------------------|  
|Preparare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|`dbcreator` Ruolo predefinito del server|  
|Creare un account di accesso del servizio Oracle CDC-SQL Server che verrà utilizzato dal servizio Oracle CDC.|`public` Ruolo predefinito del server|  
|Creare un account di accesso del servizio Oracle CDC da utilizzare per la registrazione del nuovo servizio in MSXDBCDC.|`db_datareader` e `db_datawriter` per MSXDBCDC|  
|Modificare un account di accesso del servizio Oracle CDC da utilizzare per l'aggiornamento della registrazione del servizio in MSXDBCDC.|`db_datareader` e `db_datawriter` per MSXDBCDC|  
|Eliminare un account di accesso del servizio Oracle CDC da utilizzare per l'aggiornamento della registrazione del servizio in MSXDBCDC.|`db_datareader` e `db_datawriter` per MSXDBCDC|  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server](../../integration-services/change-data-capture/connection-to-sql-server.md)   
 [Connessione a SQL Server per l'eliminazione](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md)  
  
  
