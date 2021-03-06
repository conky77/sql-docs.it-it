---
title: Creazione di stored procedure estese | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- warnings [SQL Server]
- extended stored procedures [SQL Server], debugging
- extended stored procedures [SQL Server], creating
- messages [SQL Server], extended stored procedures
ms.assetid: 9f7c0cdb-6d88-44c0-b049-29953ae75717
author: rothja
ms.author: jroth
ms.openlocfilehash: 3c22077de3bf41bc09864ac2c7f24dbdd4ecc3e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032044"
---
# <a name="creating-extended-stored-procedures"></a>Creazione di stored procedure estese
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Usare invece l'integrazione con CLR.  
  
 Una stored procedure estesa è una funzione con un prototipo:  
  
 *Xp_extendedProcName* SRVRETCODE **(** SRVPROC ** \*);**  
  
 L'utilizzo del prefisso xp_ è facoltativo. Per i nomi delle stored procedure estese viene fatta distinzione tra maiuscole e minuscole quando vi si fa riferimento in istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)], indipendentemente dalla tabella codici o dall'ordinamento installato nel server. Quando si compila una DLL:  
  
-   Se è necessario un punto di ingresso, scrivere una funzione DllMain.  
  
     Questa funzione è facoltativa e, se non viene specificata nel codice sorgente, il compilatore collega la propria versione, che si limita a restituire TRUE. Se si specifica una funzione DllMain, il sistema operativo chiama questa funzione quando un thread o un processo viene collegato alla DLL o scollegato dalla DLL.  
  
-   Tutte le funzioni chiamate dall'esterno della DLL, ovvero tutte le funzioni Efunction delle stored procedure estese, devono essere esportate.  
  
     È possibile esportare una funzione elencando il nome nella sezione Esporta di un file con estensione def oppure è possibile anteporre il nome della funzione nel codice sorgente con __declspec (dllexport), un'estensione del compilatore Microsoft (si noti che \__declspec () inizia con due caratteri di sottolineatura.  
  
 I file seguenti sono necessari per la creazione della DLL di una stored procedure estesa.  
  
|File|Descrizione|  
|----------|-----------------|  
|Srv.h|File di intestazione dell'API della stored procedure estesa|  
|Opends60.lib|Libreria di importazione per Opends60.dll|  
  
 Per creare la DLL di una stored procedure estesa, creare un progetto di tipo DLL. Per ulteriori informazioni sulla creazione di una DLL, vedere la documentazione dell'ambiente di sviluppo.  
  
 È estremamente consigliabile fare in modo che tutte le DLL delle stored procedure estese implementino ed esportino la funzione seguente:  
  
```  
__declspec(dllexport) ULONG __GetXpVersion()  
{  
   return ODS_VERSION;  
}  
```  
  
> [!NOTE]  
>  __declspec(dllexport) è un'estensione del compilatore specifica di Microsoft. Se il compilatore non supporta questa direttiva, è necessario esportare questa funzione all'interno della sezione EXPORTS nel file DEF.  
  
 Quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene avviato con il flag di traccia-T260 o se un utente con privilegi di amministratore di sistema esegue DBCC TRACEON (260) e se la DLL stored procedure estesa non supporta __GetXpVersion (), viene visualizzato un messaggio di avviso (errore 8131: la dll di stored procedure estesa \_'%' non Esporta _GetXpVersion (). viene stampato nel log degli errori di. Si noti che \__GetXpVersion () inizia con due caratteri di sottolineatura.  
  
 Se la DLL della stored procedure estesa consente l'esportazione di __GetXpVersion() ma la versione restituita dalla versione è precedente rispetto a quella richiesta dal server, nel log degli errori viene stampato un messaggio di avviso indicante la versione restituita dalla funzione e la versione prevista dal server. Se si riceve questo messaggio, viene restituito un valore non corretto da \__GetXpVersion () o si sta eseguendo la compilazione con una versione precedente di SRV. h.  
  
> [!NOTE]  
>  SetErrorMode, una funzione [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32, non deve essere chiamata nelle stored procedure estese.  
  
 Una stored procedure estesa con esecuzione prolungata deve piuttosto chiamare srv_got_attention periodicamente in modo che la procedura possa terminare se stessa in caso di interruzione della connessione o del batch.  
  
 Per eseguire il debug della DLL di una stored procedure estesa, copiare la DLL nella directory [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn. Per specificare il file eseguibile per la sessione di debug, immettere il percorso e il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nome del file eseguibile, ad esempio c:\Programmi\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Binn\Sqlservr.exe). Per informazioni sugli argomenti sqlservr, vedere [applicazione sqlservr](../../tools/sqlservr-application.md).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_got_attention &#40;API stored procedure estesa&#41;](../../relational-databases/extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
