---
title: Distribuzione del driver JDBC | Microsoft Docs
ms.custom: ''
ms.date: 01/20/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 99ca0fab9a23689ac9c20cad6ebf0d94dd7b2113
ms.sourcegitcommit: 4b2c9d648b7a7bdf9c3052ebfeef182e2f9d66af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "77004680"
---
# <a name="deploying-the-jdbc-driver"></a>Distribuzione del driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si distribuisce un'applicazione che dipende da [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], è necessario ridistribuire il driver JDBC insieme all'applicazione. Diversamente da Windows Data Access Components (Windows DAC), che è un componente del sistema operativo Windows, il driver JDBC è considerato un componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Esistono due approcci per la distribuzione del driver JDBC con l'applicazione. Un approccio prevede l'inclusione dei file del driver JDBC come parte del pacchetto di installazione personalizzato. Il secondo approccio prevede l'usp del pacchetto di installazione JDBC fornito da Microsoft, scaricabile in [Microsoft JDBC Driver per SQL Server](https://go.microsoft.com/fwlink/?LinkId=70166).  
  
 Nelle sezioni seguenti viene descritto come utilizzare il pacchetto di installazione JDBC in sistemi operativi Windows e UNIX.  
  
> [!NOTE]  
>  Per informazioni generali sulla distribuzione di applicazioni Java, vedere il sito Web Java.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Distribuzione del driver JDBC in sistemi Windows  
 Per distribuire il driver JDBC in sistemi operativi Windows, è necessario decomprimere il pacchetto di installazione compresso, denominato in genere `sqljdbc_<version>_<language>.zip`.

## <a name="deploying-the-driver-on-unix-systems"></a>Distribuzione del driver in sistemi UNIX 
 Quando il driver JDBC viene distribuito in sistemi operativi UNIX, è necessario usare la versione del file GZIP del pacchetto di installazione, denominata in genere `sqljdbc_<version>_<language>.tar.gz`.  
  
 Prima di installare il driver JDBC, assicurarsi che entrambe le utilità GZIP e TAR siano installate nel sistema operativo dell'utente e che le cartelle che contengono i file eseguibili di entrambe le utilità siano state aggiunte alla variabile di ambiente PATH.  
  
 Per decomprimere il file con estensione tar compresso, passare alla directory in cui si desidera decomprimere il driver e digitare il comando seguente:  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 Per decomprimere il file con estensione tar, spostarlo nella directory in cui si desidera installare il driver e digitare il comando seguente:  
  
 `tar -xf sqljdbc_<version>_<language>.tar`  

## <a name="legalities-of-driver-redistribution"></a>Note legali sulla ridistribuzione dei driver

Le versioni 6.0, 6.2, 6.4, 7.0, 7.2, 7.4 e 8.2 del driver JDBC sono ridistribuibili. Esaminare la clausola _Codice distribuibile_ nei contratti di licenza.

Le versioni 4.x del driver JDBC sono obsolete. Il supporto per 4.x è scaduto prima del 2018.

## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
