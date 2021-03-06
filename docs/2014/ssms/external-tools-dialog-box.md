---
title: Finestra di dialogo Strumenti esterni | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- adding external tools
- external tools [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], external tools
ms.assetid: ba797203-24d0-4922-9b97-8ab483f1db14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dc8f54bc4f6e7aaffa5d912fc9bc8f03fad71d03
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63245639"
---
# <a name="external-tools-dialog-box"></a>Finestra di dialogo Strumenti esterni
  Utilizzare la finestra di dialogo **strumenti esterni** per aggiungere strumenti esterni, ad esempio sqlcmd o blocco note, al menu **strumenti** . L' [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] aggiunta di strumenti esterni consente di avviare facilmente altre applicazioni mentre si lavora nell'ambiente. Durante l'avvio dello strumento, è possibile specificare argomenti e una directory di lavoro. L'output di alcuni strumenti può inoltre essere visualizzato nella finestra **Output** . La finestra di dialogo **Strumenti esterni** è accessibile dal menu **Strumenti** .  
  
## <a name="options"></a>Opzioni  
 **Contenuto menu**  
 Elenca i titoli degli elementi attualmente aggiunti al menu **Strumenti** . Usare i pulsanti **Sposta su** e **Sposta giù** per cambiare l'ordine di visualizzazione delle voci nel menu. Usare il pulsante **Elimina** per rimuovere una voce dal menu.  
  
 **Sposta su**  
 Sposta lo strumento selezionato più in alto nell'elenco degli strumenti visualizzati nel menu **Strumenti** .  
  
 **Sposta giù**  
 Sposta lo strumento selezionato più in basso nell'elenco degli strumenti visualizzati nel menu **Strumenti** .  
  
 **Aggiungere**  
 Consente di cancellare il contenuto delle caselle di testo e quindi di specificare un nuovo strumento.  
  
 **Elimina**  
 Rimuove lo strumento o il comando dall'elenco **Contenuto menu** e dal menu **Strumenti** .  
  
 **Titolo**  
 Consente di immettere il nome dello strumento o del comando che verrà visualizzato nel sottomenu **Strumenti esterni** del menu **Strumenti** . Inserire una e commerciale (&) prima di una lettera contenuta nel nome dello strumento per specificare tale lettera come tasto di scelta rapida. Ad esempio, "&SQLCMD" verrà visualizzato come SQLCMD nel menu **Strumenti**.  
  
 **Comando**  
 Specificare il percorso del file da avviare.  
  
 **Argomenti**  
 Consente di specificare le variabili passate allo strumento quando questo viene selezionato dal menu. Negli argomenti possono essere specificati valori che vengono passati allo strumento o al comando all'avvio. Un valore può ad esempio specificare un nome di file o una directory. Per selezionare un argomento da un elenco di argomenti predefiniti, utilizzare il pulsante freccia. È possibile aggiungere più argomenti. Per un elenco completo degli argomenti predefiniti e delle relative definizioni, vedere [Strumenti esterni - Argomenti](menu-help/external-tools.md). È inoltre possibile immettere argomenti personalizzati, ad esempio opzioni della riga di comando, a seconda del comando o dello strumento utilizzato.  
  
 **Usa finestra di output**  
 Consente di aprire la finestra di output di [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] per visualizzare l'output del comando in esecuzione. Non tutti gli strumenti hanno un formato di output che può essere visualizzato nella finestra di output. Per altre informazioni, vedere [Finestra di output](../relational-databases/scripting/transact-sql-debugger-output-window.md).  
  
 **Considera output come Unicode**  
 Interpreta output come Unicode.  
  
 **Directory iniziale**  
 Consente di specificare la directory di lavoro dello strumento. Per selezionare directory, utilizzare il pulsante freccia. È possibile selezionare più directory.  
  
 **Richiedi argomenti**  
 Consente di visualizzare la finestra di dialogo **Argomenti** che permette di immettere o modificare valori per gli argomenti ogni volta che si avvia uno strumento esterno.  
  
 **Chiudi all'uscita**  
 Chiude la finestra aperta dallo strumento quando viene chiuso lo strumento stesso.  
  
## <a name="example"></a>Esempio  
 Immettendo i seguenti valori nella finestra di dialogo **Strumenti esterni** verrà creata una voce di menu con etichetta "DAC" che, quando selezionata, consentirà di aprire un prompt dei comandi e di eseguire l'utilità **sqlcmd** usando la connessione amministrativa dedicata.  
  
|Box|valore|  
|---------|-----------|  
|**Titolo**|DAC|  
|**Comando**|
  [!INCLUDE[ssInstallPath](../includes/ssinstallpath-md.md)]Tools\Binn\SQLCMD.exe|  
|**Argomenti**|-A|  
  
## <a name="see-also"></a>Vedere anche  
 [Argomenti per gli strumenti esterni](menu-help/external-tools.md)   
 [Elementi generali dell'interfaccia utente](general-user-interface-elements.md)  
  
  
