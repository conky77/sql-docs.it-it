---
title: Modifica etichette (SQL Server componenti aggiuntivi Data mining) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f7d0accb835eb7da23ade6aec405066204fc415
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175600"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a>Modifica etichette (componenti aggiuntivi Data mining di SQL Server)
  ![Icona di Office 13 per lo strumento Modifica etichette](media/dm13-relabel.gif "Icona di Office 13 per lo strumento Modifica etichette")

 Il client di data mining per Excel consente di creare nuove etichette per i dati per semplificare la comprensione dei risultati dell'analisi.

 I motivi di modifica delle etichette includono:

-   I dati includono i risultati che sono stati codificati, ad esempio 1 per maschio e 2 per femmina.

-   Sono valori numerici di bucket e si desidera fornire agli intervalli un nome descrittivo.

-   Si desidera semplificare i nomi lunghi.

## <a name="using-the-relabel-wizard"></a>Utilizzo della procedura guidata Modifica etichette

1.  Sulla barra multifunzione **data mining** fare clic su **Pulisci** e quindi selezionare **nuova etichetta**.

2.  Selezionare la tabella o l'intervallo di dati contenente i dati che si desidera correggere.

3.  Nella pagina modifica **etichette** della procedura guidata selezionare una singola colonna scegliendo la colonna nell'elenco a discesa oppure facendo clic sulla colonna nel riquadro **esempi di dati** .

     Il riquadro **esempi di dati** Mostra solo circa 50 righe di dati, ma sono campionate per assicurarsi che venga visualizzata una corretta distribuzione dei valori.

     Fare clic sull'intestazione di colonna per **conteggio** per eseguire l'ordinamento in base al conteggio di ogni valore.

     È anche possibile eseguire l'ordinamento in base alle **etichette originali**, che risulta utile se si desidera rietichettare prima tutti i valori più alti o più bassi.

4.  Nella pagina **nuova etichetta** dati della procedura guidata, esaminare i valori nella colonna **etichette originali** e decidere come si desidera raggrupparli o modificarli.

5.  Digitare un nuovo valore nella riga sotto **nuove etichette**. È inoltre possibile scegliere un valore nell'elenco dei valori esistenti. Mentre si digitano, i nuovi valori diventano disponibili per essere subito riutilizzati.

6.  Dopo aver immesso un numero sufficiente di righe, fare clic su **Avanti**. nella pagina **Seleziona destinazione** scegliere il percorso in cui verranno salvati i dati rietichettati.

    -   **Aggiungi come nuova colonna al foglio di lavoro corrente**

         Fare clic per aggiungere una nuova colonna alla tabella contenente i nuovi valori.

    -   **Copia i dati del foglio modificati in un nuovo foglio di lavoro**

         Fare clic per creare un nuovo foglio di lavoro contenente i dati aggiornati.

    -   **Modifica dati nella posizione originale**

         Fare clic per sostituire i dati originali con i nuovi valori.

## <a name="see-also"></a>Vedere anche
 [Esplorazione e pulizia dei dati](exploring-and-cleaning-data.md)


