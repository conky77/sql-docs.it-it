---
title: ODBCCONF. EXE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b70622ea038b61883ce7a5307a558a5667139fb1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "74491970"
---
# <a name="odbcconfexe"></a>ODBCCONF. EXE
ODBCCONF. exe è uno strumento da riga di comando che consente di configurare i driver ODBC e i nomi delle origini dati.  
  
> [!NOTE]  
>  ODBCCONF. exe verrà rimosso in una versione futura di Windows Data Access Components. Evitare di utilizzare questa funzionalità e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. È possibile usare i comandi di PowerShell per gestire driver e origini dati. Per ulteriori informazioni su questi comandi di PowerShell, vedere [cmdlet di Windows Data Access Components](/powershell/module/wdac).  
  
## <a name="syntax"></a>Sintassi  
  
```console  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Argomenti  
 *interruttori*  
 Zero o più opzioni switch. Per l'elenco delle opzioni disponibili, vedere la sezione Osservazioni più avanti in questo argomento.  
  
 *azione*  
 Un'azione da eseguire. Per l'elenco delle opzioni disponibili, vedere la sezione Osservazioni.  
  
## <a name="remarks"></a>Osservazioni  
 Sono disponibili le opzioni seguenti:  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|/A {*Action*}|Specificare un'azione.<br /><br /> /A è facoltativo se è specificata una sola azione.|  
|/?|Visualizza l'utilizzo per ODBCCONF. EXE.|  
|/C|L'elaborazione continua se un'azione ha esito negativo.|  
|/E|Cancella il file di risposta specificato con/F al termine dell'elaborazione.|  
|/F|Utilizzare un file di risposta, ad `odbcconf /F my.rsp`esempio.<br /><br /> My. rsp potrebbe essere simile al seguente:`REGSVR c:\my.dll`<br /><br /> /A non viene usato in un file di risposta.|  
|/H|Visualizza utilizzo (Guida). Questa opzione è uguale a/?.|  
|/L [*modalità*] *nomefile*|Inviare l'output del programma a un file in una delle tre modalità seguenti: normale (n), Verbose (v) e debug (d). La modalità di debug registra le DLL caricate da odbcconf. exe.<br /><br /> Se si specifica/L senza una modalità, il file di log sarà vuoto.<br /><br /> Ad esempio, **/LV log. txt**.|  
|/R|L'azione verrà eseguita dopo un riavvio.|  
|/S|Modalità invisibile all'utente. Non visualizzare i messaggi di errore.|  
  
 Sono disponibili le azioni seguenti:  
  
|Azione|Descrizione|  
|------------|-----------------|  
|CONFIGDRIVER *driver_name * * parametri di configurazione specifici del driver*|Carica la DLL di installazione del driver appropriata e chiama la funzione **ConfigDriver** .<br /><br /> Equivale alla [funzione SQLConfigDriver](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Ad esempio:<br /><br /> /A {CONFIGDRIVER "nome driver" "CPTimeout = 60"}<br /><br /> /A {CONFIGDRIVER "nome driver" "DriverODBCVer = 03.80"}|  
|CONFIGDSN *driver_name* DSN =*nome* &#124; *attributi*|Aggiunge o modifica un'origine dati di sistema.<br /><br /> Equivale alla [funzione SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Ad esempio:<br /><br /> /A {CONFIGDSN "SQL Server" "DSN = nome &#124; Server = srv"}|  
|CONFIGSYSDSN *driver_name* DSN =*nome* &#124; *attributi*|Aggiunge o modifica un'origine dati di sistema.<br /><br /> Equivale alla [funzione SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Ad esempio:<br /><br /> /A {CONFIGSYSDSN "SQL Server" "DSN = nome &#124; Server = srv"}|  
|INSTALLDRIVER|Equivale alla [funzione SQLInstallDriverEx](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Per informazioni sulla sintassi delle coppie parola chiave/valore passata a INSTALLDRIVER, vedere [sottochiavi di specifica del driver](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Ad esempio:<br /><br /> /A {INSTALLDRIVER "driver &#124; driver = c:\your.dll &#124; Setup = c:\your.dll &#124; APILevel = 2 &#124; ConnectFunctions = YYY &#124; DriverODBCVer = 03.50 &#124; fileusage = 0 &#124; sqllevel = 1"}|  
|*Percorso driver * * configurazione conversione* INSTALLTRANSLATOR|Aggiunge informazioni su un convertitore al **HKEY_LOCAL_MACHINE \software\odbc\odbcinst. **Chiave del registro di sistema INI\ODBC Translator.<br /><br /> Equivale alla [funzione SQLInstallTranslatorEx](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Per informazioni sulla sintassi delle coppie parola chiave/valore passata a INSTALLDRIVER, vedere [sottochiavi di specifica di Translator](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Ad esempio:<br /><br /> /A {INSTALLTRANSLATOR "traduttore &#124; Translator = c:\My.dll &#124; Setup = c:\My.dll"}|  
|*Dll* regsvr|Registra una DLL.<br /><br /> Equivalente a regsvr32. exe.<br /><br /> Ad esempio:<br /><br /> /A {REGSVR c:\My.dll}|  
|SETFILEDSNDIR|Quando HKEY_LOCAL_MACHINE \SOFTWARE\ODBC\ODBC. Il file INI\ODBC DSN\DefaultDSNDir non esiste, l'azione SETFILEDSNDIR la crea e assegna al valore HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir, accodato con le origini \ODBC\Data.<br /><br /> Valore HKEY_LOCAL_MACHINE \SOFTWARE\ODBC\ODBC. INI\ODBC file DSN\DefaultDSNDir specifica il percorso predefinito utilizzato dall'amministratore dell'origine dati ODBC durante la creazione di un'origine dati basata su file.<br /><br /> Ad esempio:<br /><br /> /A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>Vedere anche  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
