---
title: Installazione del driver OLE DB per SQL Server| Microsoft Docs
description: Installazione e disinstallazione di OLE DB Driver per SQL Server
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, uninstalling
- MSOLEDBSQL, installing
- MSOLEDBSQL, uninstalling
- Setup [OLE DB Driver for SQL Server]
- uninstalling OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], uninstalling OLE DB Driver for SQL Server
- installing OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, installing
- data access [OLE DB Driver for SQL Server], installing OLE DB Driver for SQL Server
- removing OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 08f33d84ee8c035e1e1d3818e2a036f96af2a280
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "67989313"
---
# <a name="installing-ole-db-driver-for-sql-server"></a>Installazione del driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Per installare OLE DB Driver per SQL Server è necessario il programma di installazione msoledbsql.msi.
Eseguire il programma di installazione ed effettuare le selezioni preferite. OLE DB Driver per SQL Server può essere installato side-by-side con le versioni precedenti dei provider Microsoft OLE DB.

I file di OLE DB Driver per SQL Server (msoledbsql.dll, msoledbsqlr.rll) sono installati in `%SYSTEMROOT%\system32\`. Inoltre, il file msoledbsql.msi x64 installa i file binari a 32 bit in `%SYSTEMROOT%\SysWOW64\`.

> [!NOTE]  
> Tutte le impostazioni del Registro di sistema appropriate per OLE DB Driver per SQL Server vengono definite durante il processo di installazione.  

I file di intestazione e di libreria di OLE DB Driver per SQL Server (msoledbsql.h e msoledbsql.lib) sono installati in `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`. Inoltre, il file msoledbsql.msi x64 installa gli stessi file in `%PROGRAMFILES(x86)%\Microsoft SQL Server\Client SDK\OLEDB\182\SDK`.  

È possibile distribuire OLE DB driver per SQL Server usando msoledbsql.msi. Potrebbe essere necessario installare OLE DB Driver per SQL Server quando si distribuisce un'applicazione. Un modo per installare più pacchetti in un'installazione che all'utente può sembrare singola consiste nell'usare la tecnologia del chainer e del programma di avvio automatico. Per ulteriori informazioni, vedere [Authoring a Custom Bootstrapper Package for Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) (informazioni in lingua inglese) e [Aggiunta di prerequisiti personalizzati](https://go.microsoft.com/fwlink/?LinkId=115668).  
  
Il file msoledbsql.msi x64 installa anche la versione a 32 bit di OLE DB Driver per SQL Server. Se l'applicazione è destinata a una piattaforma diversa da quella su cui è stata sviluppata, è possibile scaricare le versioni di msoledbsql.msi per x64 e x86.

Quando si richiama msoledbsql.msi, solo i componenti client vengono installati per impostazione predefinita. I componenti client sono file che supportano l'esecuzione di un'applicazione sviluppata tramite il driver OLE DB per SQL Server. Per installare i componenti SDK, specificare `ADDLOCAL=All` sulla riga di comando. Ad esempio:  

`msiexec /i msoledbsql.msi ADDLOCAL=ALL`  

## <a name="silent-install"></a>Installazione invisibile all'utente  
 Se si utilizza l'opzione /passive, /qn, /qb o /qr con msiexec, è necessario specificare anche IACCEPTMSOLEDBSQLLICENSETERMS=YES per indicare in modo esplicito l'accettazione delle condizioni di licenza dell'utente finale. È necessario specificare questa opzione in lettere maiuscole.  

## <a name="installing-ole-db-driver-for-sql-server-as-a-dependency"></a>Installazione di OLE DB Driver per SQL Server come dipendenza  
È importante non disinstallare OLE DB Driver per SQL Server finché tutte le applicazioni dipendenti non vengono disinstallate. Per visualizzare per gli utenti un avviso che indica che l'applicazione dipende da OLE DB Driver per SQL Server, usare l'opzione di installazione APPGUID in MSI, come riportato di seguito:  

 `msiexec /i msoledbsql.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  

Il valore passato a APPGUID è il codice prodotto specifico. Quando si utilizza Microsoft Installer per aggregare il programma di installazione dell'applicazione, è necessario creare un codice prodotto.
L'opzione APPGUID richiede l'esecuzione del programma di installazione da un prompt dei comandi con privilegi elevati.

## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con il driver OLE DB per SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
