---
title: Aggiungere o eliminare un indicatore (Generatore report) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 08dd396fc68bae04d973d6b96f67466006642120
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081569"
---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a>Aggiungere o eliminare un indicatore (Generatore report e SSRS)
  In un report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , gli indicatori sono piccoli misuratori sui quali è possibile leggere immediatamente lo stato di un singolo valore di dati. Per altre informazioni in merito, vedere [Indicatori &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md).  
  
 Gli indicatori sono posizionati comunemente nelle celle di una tabella o di una matrice, ma possono essere utilizzati anche separatamente, affiancati ai misuratori o incorporati nei misuratori.  
  
 Quando si aggiunge un indicatore per la prima volta, viene configurato per impostazione predefinita in modo da utilizzare le percentuali come unità di misura. Gli intervalli delle percentuali sono distribuiti uniformemente tra i membri del set di indicatori e l'ambito di valori mostrati dall'indicatore rappresenta l'elemento padre dell'indicatore, ad esempio una tabella o una matrice.  
  
 È possibile aggiornare i valori e gli stati di indicatori. Per altre informazioni, vedere gli argomenti seguenti:  
  
-   [Modificare le icone degli indicatori e dei set di indicatori &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [Impostare e configurare le unità di misura &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [Impostare l'ambito di sincronizzazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/set-synchronization-scope-report-builder-and-ssrs.md)  
  
 Poiché un indicatore viene posizionato nel pannello del misuratore, è necessario selezionare l'indicatore anziché il pannello quando si vuole configurare l'indicatore tramite la finestra di dialogo **Proprietà indicatori** o il riquadro **Proprietà** . Nell'immagine seguente viene mostrato un indicatore selezionato nel relativo pannello del misuratore.  
  
 ![rs_GaugePanelWithIndicator](../../reporting-services/report-design/media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")  
  
> [!NOTE]  
>  A seconda della larghezza della colonna e della lunghezza dei valori di dati, il testo nella tabella o nelle celle della matrice potrebbe essere sottoposto a wrapping ed essere quindi visualizzato su più righe. In tal caso, l'icona dell'indicatore potrebbe essere adattata e assumere una forma diversa rendendola così meno leggibile. Posizionare l'indicatore in un rettangolo per assicurarsi che l'icona non sia mai adattata.  
  
## <a name="to-add-an-indicator-to-a-table-or-matrix"></a>Per aggiungere un indicatore a una tabella o a una matrice  
  
1.  Aprire un report esistente o crearne uno nuovo contenente una tabella e una matrice con i dati che si desidera visualizzare. Per altre informazioni, vedere [Tabelle &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md) o [Matrici](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md).  
  
2.  Inserire una colonna nella tabella o nella matrice. Per altre informazioni, vedere [Inserire o eliminare una colonna &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Facoltativamente, nella scheda **Inserisci** fare clic su **Rettangolo**e quindi fare clic su una cella nella nuova colonna.  
  
4.  Nella scheda **Inserisci** fare clic su **Indicatore**e quindi fare clic su una cella nella nuova colonna.  
  
     Se è stato aggiunto un rettangolo a una cella, fare clic su quella cella.  
  
5.  Nel riquadro sinistro della finestra di dialogo **Seleziona tipo indicatore** fare clic sul tipo di indicatore desiderato e quindi sul set di indicatori.  
  
6.  Fare clic su **OK**.  
  
7.  Fare clic sull'indicatore. Viene visualizzato il riquadro **Dati del misuratore** .  
  
8.  Nell'area **Valori** , nell'elenco a discesa **(valore non specificato)** , fare clic sul campo di cui si vuole visualizzare i valori come un indicatore.  
  
     L'indicatore è configurato per utilizzare valori predefiniti. Per impostazione predefinita, gli indicatori vengono configurati per utilizzare le percentuali come unità di misura e gli intervalli di percentuale sono distribuiti uniformemente tra i membri dell'indicatore; il valore mostrato dall'indicatore utilizza l'ambito del gruppo più vicino.  
  
## <a name="to-delete-an-indicator-to-a-table-or-matrix"></a>Per eliminare un indicatore in una tabella o in una matrice  
  
1.  Fare clic con il pulsante destro del mouse sull'indicatore da eliminare e scegliere **Elimina**.  
  
    > [!NOTE]  
    >  È probabile che un indicatore sia posizionato in un pannello del misuratore che contiene altri indicatori o misuratori. Se i pannelli del misuratore contengono più elementi, assicurarsi di fare clic sull'indicatore da eliminare e non sul pannello del misuratore. Se si fa clic e quindi si elimina il pannello del misuratore, verranno eliminati i pannelli del misuratore e tutti gli elementi in esso contenuti.  
  
2.  Fare clic su **Elimina**.  
  
## <a name="see-also"></a>Vedere anche  
 [Indicatori &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  
