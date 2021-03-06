---
title: Effetti delle opzioni ISO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebef85cf1deb2327122edfd536991f689b14c747
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206757"
---
# <a name="effects-of-iso-options"></a>Effetti delle opzioni ISO
  Lo standard ODBC è molto simile allo standard ISO e le applicazioni ODBC presuppongono un comportamento standard da un driver ODBC. Per garantire la conformità del comportamento con quello definito nello standard ODBC, il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC di Native client utilizza sempre le opzioni ISO disponibili nella versione di SQL Server a cui si connette.  
  
 Quando il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC di Native client si connette a un' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]istanza di, il server rileva che il client utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] il driver ODBC di Native client e imposta diverse opzioni in.  
  
 Il driver stesso genera queste istruzioni, senza alcuna richiesta da parte dell'applicazione ODBC. L'impostazione di queste opzioni rende più portabili le applicazioni ODBC che utilizzano il driver in quanto il comportamento del server corrisponde allo standard ISO.  
  
 Nelle applicazioni DB-Library in genere queste opzioni non vengono attivate. I siti che osservano un comportamento diverso tra i client ODBC o DB-Library quando si esegue la stessa istruzione SQL non devono presupporre che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] questo indichi un problema con il driver ODBC di Native Client. È necessario eseguire prima di tutto l'istruzione nell'ambiente DB-Library con le stesse opzioni SET utilizzate dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 Poiché le opzioni SET possono essere attivate e disattivate in qualsiasi momento da utenti e applicazioni, gli sviluppatori di stored procedure e trigger devono testare anche le stored procedure e i trigger con le opzioni SET sopra indicate attivate e disattivate per garantirne il corretto funzionamento indipendentemente dalle opzioni impostate da una connessione specifica quando il trigger o la stored procedure viene richiamata. Un trigger o una stored procedure in cui è necessario impostare una di queste opzioni in modo specifico deve generare un'istruzione SET all'inizio del trigger o della stored procedure stessa. Questa istruzione SET rimarrà attiva soltanto durante l'esecuzione del trigger o della stored procedure. Al completamento della stessa, verrà ripristinata l'impostazione originale.  
  
 Durante la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], viene attivata anche una quarta opzione SET, CONCAT_NULL_YIELDS_NULL. Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC di Native client non imposta queste opzioni su se ANSINPW = no è specificato nell'origine dati o in [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) o [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md).  
  
 Analogamente alle opzioni ISO indicate in precedenza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , il driver ODBC di Native client non attiva l'opzione QUOTED_IDENTIFIER in se QUOTEDID = no è specificato nell'origine dati o in **SQLDriverConnect** o **SQLBrowseConnect**.  
  
 Per consentire al driver di conoscere lo stato corrente delle opzioni SET, le applicazioni ODBC non devono utilizzare l'istruzione SET [!INCLUDE[tsql](../../../includes/tsql-md.md)] per impostarle. Per eseguire questa operazione, infatti, devono utilizzare solo le opzioni dell'origine dati o della connessione. Se l'applicazione genera istruzioni SET, il driver può generare istruzioni SQL errate.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di istruzioni &#40;ODBC&#41;](executing-statements-odbc.md)   
 [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
  
