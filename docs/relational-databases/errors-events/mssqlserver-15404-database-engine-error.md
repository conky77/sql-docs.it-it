---
title: MSSQLSERVER_15404 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15404 (Database Engine error)
ms.assetid: 69677f02-bc81-4e4a-99b8-5c1bd1de36df
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: caa8f9a9de287b5628518c286a1c411d10d7f7fd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "67908556"
---
# <a name="mssqlserver_15404"></a>MSSQLSERVER_15404
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|15404|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SEC_NTGRP_ERROR|  
|Testo del messaggio|Non è stato possibile ottenere informazioni relative al gruppo/utente di Windows NT '*user*', codice di errore *code*.|  
  
## <a name="explanation"></a>Spiegazione  
L'errore 15404 è utilizzato nell'autenticazione quando si specifica un'entità non valida. In alternativa, la rappresentazione di un account di Windows ha esito negativo poiché non esiste alcuna relazione di trust completo tra l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il dominio dell'account di Windows.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare che l'entità di Windows esista e non siano stati commessi errori di digitazione.  
  
Se questo errore è dovuto all'assenza di una relazione di trust completo tra l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il dominio dell'account di Windows, è possibile risolvere il problema tramite una delle azioni seguenti:  
  
-   Utilizzare un account dello stesso dominio dell'utente di Windows per il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza un account computer, ad esempio Servizio di rete o Sistema locale, il computer deve essere considerato attendibile dal dominio che contiene l'utente di Windows.  
  
-   Utilizzare un account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
