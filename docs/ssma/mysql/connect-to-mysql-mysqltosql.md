---
title: Connettersi a MySQL (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 94099d01-ab19-4d58-a172-340c86b4a0f3
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 3fe4b59a5131838357d7f58e5333e0ba6b9c80f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103228"
---
# <a name="connect-to-mysql-mysqltosql"></a>Connettersi a MySQL (MySQLToSQL)
Usare la finestra di dialogo **Connetti a MySQL** per connettersi al database MySQL di cui si vuole eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere **Connetti a MySQL**dal menu **file** . Se è già stata effettuata la connessione, il comando viene **riconnesso a MySQL**.  
  
## <a name="options"></a>Opzioni  
**Provider**  
  
Il provider MySQL disponibile è il driver MySQL ODBC 5,1 (attendibile).  
  
**Mode**  
  
La modalità predefinita è la modalità standard. In modalità standard immettere o selezionare i valori per MySQL, nome server, porta server, nome utente e password.  
  
**Nome server**  
  
Immettere il nome del server MySQL. Si tratta di un'opzione della modalità standard.  
  
**Porta server**  
  
Immettere la porta del server. La porta predefinita del server è 3306. Si tratta di un'opzione della modalità standard.  
  
**Nome utente**  
  
Immettere il nome utente che SSMA userà per connettersi al database MySQL.  
  
**Password**  
  
Immettere il nome utente e la password  
  
**SSL**  
  
Se si desidera connettersi in modo sicuro a MySQL, utilizzare Secure Socket Layer (SSL) selezionando la casella di controllo **SSL** .  
  
**Configurare**  
  
Offre un'opzione per configurare la connessione a MySQL tramite Secure Socket Layer (SSL).  
  
> [!NOTE]  
> Per abilitare la **configurazione**, è necessario che SSL sia impostato su **true**.  
  
Quando si fa clic sul pulsante "Configura", viene visualizzata una finestra di dialogo. Per usare la crittografia durante la connessione al database MySQL, è necessario definire il percorso dei seguenti tre file di certificato presenti nella finestra di dialogo [Privacy Enhanced Mail Certificates (PEM)]:  
  
-   **Autorità di certificazione SSL:** Specifica il percorso di un file con un elenco di CA SSL attendibili.  
  
-   **Certificato SSL:** Specifica il nome del file di certificato SSL da usare per stabilire una connessione protetta.  
  
-   **chiave SSL:** Specifica il nome del file di chiave SSL da usare per stabilire una connessione protetta.  
  
> [!NOTE]  
> -   Il pulsante **OK** è abilitato quando sono state fornite le informazioni necessarie. Se uno dei percorsi di file non è valido, il pulsante "OK" rimarrà disabilitato.  
> -   Il pulsante **Annulla** chiude la finestra di dialogo e **Disattiva** l'opzione SSL dal form principale della connessione.  
  
