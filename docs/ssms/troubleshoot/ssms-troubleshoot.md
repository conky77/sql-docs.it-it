---
title: Risoluzione dei problemi relativi a un blocco o a un arresto anomalo con SSMS
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: dnethi
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 09/18/2019
ms.openlocfilehash: f994a44d6fe0f458ae8f8d8be0351421322e7967
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "75243876"
---
# <a name="get-diagnostic-data-after-a-sql-server-management-studio-ssms-crash"></a>Ottenere dati di diagnostica dopo un arresto anomalo di SQL Server Management Studio (SSMS)

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

## <a name="get-full-memory-dump-after-a-hang-or-crash"></a>Ottenere il dump della memoria completo dopo un blocco o un arresto anomalo del sistema

Ottenere un dump della memoria completo di SQL Server Management Studio (SSMS) in seguito a un blocco o un arresto anomalo.

Per acquisire le informazioni di diagnostica per risolvere i problemi di un arresto anomalo o un blocco di SSMS, seguire questa procedura.

1. Scaricare [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Decomprimere il download in una cartella.

3. Aprire il prompt dei comandi ed eseguire il comando seguente.

    ```console
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    Se viene richiesto di accettare un contratto di licenza, selezionare *Accetto*.

4. Avviare SSMS, se non è ancora stato avviato.

5. Riprodurre il problema.

6. Il testo verrà visualizzato nel prompt dei comandi relativo alla scrittura del file di dump. Attendere il completamento dell'operazione.

7. Creare una nuova cartella e copiare il file *.dmp di cui è stata eseguita la scrittura in tale cartella.

8. Copiare i file seguenti nella stessa cartella.

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Comprimere la cartella

## <a name="get-full-memory-dump-for-an-outofmemoryexception"></a>Ottenere il dump completo della memoria per un'eccezione OutOfMemoryException

Ottenere un dump completo della memoria di SSMS quando genera un'eccezione OutOfMemoryException.

È possibile ottenere un dump completo della memoria con qualsiasi eccezione gestita.

Per acquisire le informazioni di diagnostica per la risoluzione dei problemi relativi a un'eccezione di tipo OutOfMemoryException generata da SSMS, seguire questa procedura.

1. Scaricare [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Decomprimere il download in una cartella.

3. Aprire il prompt dei comandi ed eseguire il comando seguente.

    ```console
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    Se viene richiesto di accettare un contratto di licenza, selezionare *Accetto*.

4. Avviare SQL Server Management Studio, se non è ancora stato avviato.

5. Riprodurre il problema.

6. Il testo verrà visualizzato nel prompt dei comandi relativo alla scrittura del file di dump. Attendere il completamento dell'operazione.

7. Creare una nuova cartella e copiare il file *.dmp di cui è stata eseguita la scrittura in tale cartella.

8. Copiare i file seguenti nella stessa cartella.

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Comprimere la cartella.
