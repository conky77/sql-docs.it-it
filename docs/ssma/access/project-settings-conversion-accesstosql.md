---
title: Impostazioni progetto (conversione) (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- conversion, options described
- Project Settings dialog box, Conversion
ms.assetid: bcebc635-c638-4ddb-924c-b9ccfef86388
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: ff44d34e6c701c8d43260982d3117def4cb9530d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67929450"
---
# <a name="project-settings-conversion-accesstosql"></a>Impostazioni progetto (conversione) (AccessToSQL)
Le impostazioni del progetto di conversione consentono di configurare il modo in cui gli oggetti vengono [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] convertiti da oggetti di database di Access a o SQL Azure oggetti di database.  
  
Il riquadro conversione è disponibile nelle finestre di dialogo **Impostazioni progetto** e **Impostazioni progetto predefinite** .  
  
-   Utilizzare la finestra di dialogo **Impostazioni progetto** per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni di conversione, nel menu **strumenti** selezionare **Impostazioni progetto**, fare clic su **generale** nella parte inferiore del riquadro sinistro, quindi selezionare **conversione**.  
  
-   Utilizzare la finestra di dialogo **Impostazioni progetto predefinite** per impostare le opzioni di configurazione per tutti i progetti. Per accedere alle impostazioni di conversione, nel menu **strumenti** selezionare **Impostazioni progetto predefinite**, selezionare il tipo di progetto di migrazione per cui è necessario visualizzare le impostazioni/changed dall'elenco a discesa **versione destinazione migrazione** , fare clic su **generale** nella parte inferiore del riquadro a sinistra e quindi selezionare **conversione**.  
  
## <a name="options"></a>Opzioni  
**Aggiungi chiave primaria**  
Crea una nuova chiave primaria nella tabella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure se una tabella di accesso non dispone di una chiave primaria o di un indice univoco.  
  
-   **Modalità predefinita**: false  
  
-   **Modalità ottimistica**: false  
  
-   **Modalità completa**: true  
  
Quando si è connessi a SQL Azure, per impostazione predefinita è true. **Aggiungi colonne timestamp**  
Specifica se SSMA deve creare un valore di timestamp se necessario.  
  
-   **Modalità predefinita**: Let SSMA decidere  
  
-   **Modalità ottimistica**: mai  
  
-   **Modalità completa**: consente a SSMA di decidere  
  
**Includere un report di valutazione dei dati con i report di valutazione della conversione**  
Include una valutazione dei dati nel report di valutazione.  
  
-   **Modalità predefinita**: true  
  
-   **Modalità ottimistica**: false  
  
-   **Modalità completa**: true  
  
**Tipo di messaggio quando una chiave primaria include colonne nullable**  
Specifica il tipo di messaggio (avviso, errore o Nothing) che SSMA Visualizza nel riquadro di output quando trova chiavi primarie con colonne nullable.  
  
-   **Modalità predefinita**: avviso  
  
-   **Modalità ottimistica**: nessun messaggio  
  
-   **Modalità completa**: errore  
  
**Tipo di messaggio quando le colonne chiave esterna hanno dimensioni diverse**  
Specifica il tipo di messaggio (avviso, errore o Nothing) che SSMA Visualizza nel riquadro di output quando trova una chiave esterna di testo non corretta.  
  
-   **Modalità predefinita**: avviso  
  
-   **Modalità ottimistica**: nessun messaggio  
  
-   **Modalità completa**: errore  
  
**Tipo di messaggio quando le colonne di tipo Memo sono indicizzate**  
Specifica il tipo di messaggio (avviso, errore o Nothing) visualizzato da SSMA nel riquadro di output quando viene trovato un indice che contiene una colonna di tipo **Memo** .  
  
-   **Modalità predefinita**: avviso  
  
-   **Modalità ottimistica**: nessun messaggio  
  
-   **Modalità completa**: errore  
  
**Avvisa quando una query complessa usa un carattere jolly\&(#42;)**  
Visualizza un avviso nel riquadro di output e Elenco errori quando il nome di una colonna in un'istruzione SELECT è un carattere jolly (*).  
  
-   **Modalità predefinita**: true  
  
-   **Modalità ottimistica**: false  
  
-   **Modalità completa**: true  
  
**Avvisa quando viene modificato il nome dell'identificatore**  
Visualizza un messaggio nel report di valutazione e nel riquadro di output quando il nome di un identificatore di oggetto viene modificato da SSMA.  
  
-   **Modalità predefinita**: true  
  
-   **Modalità ottimistica**: false  
  
-   **Modalità completa**: true  
  
**Avvisa quando l'identificatore verrà racchiuso tra virgolette**  
Consente di visualizzare un messaggio nel report di valutazione e nel riquadro di output quando il nome di un identificatore di oggetto verrà racchiuso tra virgolette da SSMA. Gli identificatori di citazione sono necessari quando il nome è una parola chiave o contiene caratteri speciali.  
  
-   **Modalità predefinita**: true  
  
-   **Modalità ottimistica**: false  
  
-   **Modalità completa**: true  
  
## <a name="see-also"></a>Vedere anche  
[Guida di riferimento all'interfaccia utente (accesso)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
