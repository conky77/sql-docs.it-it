---
title: Matrice di compatibilità | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application compatibility issues [ODBC]
- application upgrades [ODBC], compatibility matrix
- upgrading applications [ODBC], compatibility matrix
ms.assetid: 0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 273633532b9b9247ea7aa12fe90bfcc3c6f6bb81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083270"
---
# <a name="compatibility-matrix"></a>Matrice di compatibilità
Nella tabella seguente viene descritta la compatibilità dei tipi di applicazioni e driver definiti in precedenza in questa sezione.  
  
|Tipo di applicazione<br /><br /> e versione|ODBC a 32 bit<br /><br /> driver *2. x*|ODBC *3. x*<br /><br /> driver|Driver ODBC 3,8|Driver conformi a ISO e Apri gruppo|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|applicazione a 16 bit, qualsiasi versione|Compatibile|Compatibile|Compatibile|Compatibile|  
|Applicazione pure *2. x*|Compatibile|Compatibile|Compatibile|Non compatibile [3]|  
|Applicazione ricompilata pure *2. x*|Compatibile|Compatibile [1]|Compatibile [1]|Non compatibile [3]|  
|Applicazione Unicode pure *2. x*|Compatibile|Compatibile [1]|Compatibile [1]|Non compatibile [3]|  
|Applicazione Open Group e conforme a ISO pure|Non compatibile|Compatibile [2]|Compatibile [2]|Compatibile [2]|  
|Applicazione 3,0 pure|Non compatibile|Compatibile|Compatibile|Non compatibile [4]|  
|Applicazione 3,5 pure|Non compatibile|Compatibile|Compatibile|Non compatibile [4]|  
|Applicazione pure 3,8 (o versione successiva)|Non compatibile [5]|Non compatibile [5]|Compatibile|Non compatibile [4]|  
|Applicazione sostituita|Compatibile|Compatibile|Compatibile|Non compatibile [3]|  
  
 [1] l'applicazione deve essere ricompilata con le intestazioni ODBC 3,5 (o versioni successive) con l'opzione UNICODE (se si tratta di un'applicazione Unicode) e deve impostare ODBCVER su 0x0250.  
  
 [2] l'applicazione deve essere compilata con le intestazioni ODBC 3,5 (o versione successiva) e collegarla a gestione driver ODBC. Deve inoltre impostare il flag di intestazione ODBC_STD.  
  
 [3] Questa configurazione può potenzialmente non funzionare perché sono presenti funzionalità di ODBC *2. x* che non sono incluse negli standard, ad esempio i segnalibri.  
  
 [4] Questa configurazione può potenzialmente non funzionare perché sono presenti funzionalità di ODBC *3. x* che non sono incluse negli standard, ad esempio i segnalibri.  
  
 [5] Questa configurazione può avere esito negativo perché sono presenti funzionalità di ODBC 3,8 che non si trovano in driver ODBC 2. x o 3. x, ad esempio [tipi di dati C specifici del driver in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
## <a name="driver-manager-compatibility"></a>Compatibilità di gestione driver  
 All'avvio di un'applicazione ODBC 3,0 che deve funzionare con tutte le versioni di gestione driver è necessario eseguire le operazioni seguenti:  
  
-   Allocare un handle di ambiente.  
  
-   Impostare l'attributo SQL_ATTR_ODBC_VERSION Environment su SQL_OV_ODBC3_80. Se Gestione driver restituisce SQL_ERROR, gestione driver è precedente a 3,8. Ripristinare SQL_ATTR_ODBC_VERSION SQL_OV_ODBC3 o SQL_OV_ODBC2, in base alle esigenze, per corrispondere a gestione driver.  
  
-   Allocare un handle di connessione.  
  
-   Creare una connessione.  
  
-   Chiamare SQLGetInfo per SQL_DRIVER_ODBC_VER per determinare la versione del driver. Se il driver è un driver ODBC 3,8, è possibile utilizzare i tipi C specifici del driver. In caso contrario, non usare i tipi di dati C specifici del driver.  
  
 Si noti che un'applicazione ODBC 3. x ricompilata può utilizzare funzionalità ODBC 3,8 diverse dai tipi C specifici del driver senza specificare SQL_OV_ODBC3_80 per SQL_ATTR_ODBC_VERSION. Questa operazione è simile a un'applicazione ODBC 2. x ricompilata utilizzando le funzionalità di ODBC 3. x.  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>Utilizzo di SQLCancelHandle in un'applicazione compatibile con tutti i gestori di driver  
 Poiché la [funzione SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) non è supportata nei gestori di driver rilasciati prima di Windows 7, un'applicazione non può essere caricata in versioni precedenti di Windows se chiama direttamente **SQLCancelHandle** . Per utilizzare tutte le versioni di gestione driver e utilizzare **SQLCancelHandle** nelle nuove versioni di Windows, un'applicazione deve chiamare **SQLCancelHandle** indirettamente utilizzando **LoadLibrary** e **GetProcAddress.**  
  
## <a name="see-also"></a>Vedere anche  
 [Novità di ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
