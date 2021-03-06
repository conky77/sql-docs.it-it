---
title: Impostazioni client obbligatorie | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
ms.assetid: e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bdb99cb3d792900f48ceb69c25c7ae720c339683
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922299"
---
# <a name="required-client-settings"></a>Impostazioni obbligatorie dei client
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Specificare le impostazioni seguenti per usare un gestore di **DataFactory** personalizzato.  
  
-   Specificare "provider = MS Remote" nella proprietà dell' [oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) Object [provider Property (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) o nella **stringa di connessione dell'oggetto Connection "** **provider**=".  
  
-   Impostare la proprietà [CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md) su **adUseClient**.  
  
-   Specificare il nome del gestore da utilizzare nella proprietà del **gestore** dell'oggetto [datacontrollo (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md) o nella stringa di connessione dell'oggetto [Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) "**handler**=". Non è possibile impostare il gestore nella stringa di connessione dell'oggetto **connessione** .  
  
 RDS fornisce un gestore predefinito sul server denominato **MSDFMAP. Gestore**. Il file di personalizzazione predefinito è denominato MSDFMAP. INI).  
  
 **Esempio**  
  
 Si supponga che le sezioni seguenti in **MSDFMAP. INI** e il nome dell'origine dati, AdvWorks, sono stati definiti in precedenza:  
  
```console
[connect CustomerDataBase]  
Access=ReadWrite  
Connect="DSN=AdvWorks"  
  
[sql CustomerById]  
SQL="SELECT * FROM Customers WHERE CustomerID = ?"  
```  
  
 I frammenti di codice seguenti sono scritti in Visual Basic:  
  
## <a name="rdsdatacontrol-version"></a>RDS. Versione di DataControl  
  
```vb
Dim dc as New RDS.DataControl  
Set dc.Handler = "MSDFMAP.Handler"  
Set dc.Server = "https://yourServer"  
Set dc.Connect = "Data Source=CustomerDatabase"  
Set dc.SQL = "CustomerById(4)"  
dc.Refresh  
```  
  
## <a name="recordset-version"></a>Versione recordset  
  
```vb
Dim rs as New ADODB.Recordset  
rs.CursorLocation = adUseClient  
```  
  
 Specificare la proprietà o la parola chiave [handler (RDS)](../../../ado/reference/rds-api/handler-property-rds.md) ; Proprietà o parola chiave del [provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) ; e gli identificatori *CustomerByID* e *CustomerDatabase* . Aprire quindi l'oggetto **Recordset**  
  
 RS. Aprire "CustomerById (4)", "Handler = MSDFMAP. Gestore; "& _  
  
```vb
"Provider=MS Remote;Data Source=CustomerDatabase;" & _  
"Remote Server=https://yourServer"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sezione connessione file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Sezione SQL del file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Sezione utenti del file di personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalizzazione di datafactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni client obbligatorie](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Informazioni sul file di personalizzazione](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)   
 [Scrittura di un gestore personalizzato](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)

