---
title: Eseguire istruzione per istruzione il codice Transact-SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, debugging code
- Transact-SQL debugger, step over
- Transact-SQL debugger, step out
- Transact-SQL debugger, step into
ms.assetid: e09079b8-c4c9-42b4-821b-4ce81a98a086
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1a125bdb345f8e3760560638a137ff160821bd1b
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643272"
---
# <a name="step-through-transact-sql-code"></a>Esecuzione istruzione per istruzione del codice Transact-SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] consente di controllare quali istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] vengono eseguite in una finestra dell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] . È possibile sospendere l'esecuzione del debugger in corrispondenza di singole istruzioni e successivamente visualizzare lo stato degli elementi di codice in quei punti.  
  
## <a name="breakpoints"></a>Punti di interruzione  
 Un punto di interruzione indica al debugger di sospendere temporaneamente l'esecuzione in corrispondenza di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] specifica. Per altre informazioni sui punti di interruzione, vedere [Punti di interruzione Transact-SQL](../../relational-databases/scripting/transact-sql-breakpoints.md).  
  
## <a name="controlling-statement-execution"></a>Controllo dell'esecuzione di istruzioni  
 Nel debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] è possibile specificare le opzioni seguenti per eseguire il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] dall'istruzione corrente:  
  
-   Eseguire il codice fino al successivo punto di interruzione.  
  
-   Eseguire la successiva istruzione.  
  
     Se l'istruzione successiva richiama una stored procedure, una funzione o un trigger [!INCLUDE[tsql](../../includes/tsql-md.md)] , verrà visualizzata dal debugger una nuova finestra dell'editor di query contenente il codice del modulo. La finestra sarà in modalità di debug e l'esecuzione verrà sospesa in corrispondenza della prima istruzione nel modulo. È possibile spostarsi quindi nel codice del modulo, ad esempio, impostando dei punti di interruzione o avanzando istruzione per istruzione nel codice.  
  
-   Passare all'istruzione successiva.  
  
     Viene eseguita l'istruzione successiva. Tuttavia, se l'istruzione richiama una stored procedure, una funzione o un trigger, il codice del modulo viene eseguito fino alla fine e i risultati vengono restituiti al codice che ha effettuato la chiamata. Se si è sicuri che in una stored procedure non vi siano errori, è possibile superarla. L'esecuzione viene sospesa in corrispondenza dell'istruzione che segue la chiamata alla stored procedure, la funzione o il trigger.  
  
-   Uscire da una stored procedure, una funzione o un trigger.  
  
     L'esecuzione viene sospesa in corrispondenza dell'istruzione che segue la chiamata alla stored procedure, la funzione o il trigger.  
  
-   Eseguire il codice dalla posizione corrente alla posizione corrente del puntatore e ignorare tutti i punti di interruzione.  
  
 Nella tabella seguente sono elencate le varie procedure che consentono di controllare il modo in cui le istruzioni sono eseguite nel debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
|Azione|Azione da eseguire:|  
|------------|---------------------|  
|Eseguire tutte le istruzioni dall'istruzione corrente al successivo punto di interruzione|Fare clic su **Continua** nel menu **Debug** .<br /><br /> Fare clic sul pulsante **Continua** sulla barra degli strumenti **Debug** .|  
|Eseguire la successiva istruzione o il successivo modulo.|Fare clic su **Esegui istruzione** nel menu **Debug** .<br /><br /> Fare clic sul pulsante **Esegui istruzione** sulla barra degli strumenti **Debug** .<br /><br /> Premere F11.|  
|Passare alla successiva istruzione o al successivo modulo.|Fare clic su **Esegui istruzione/routine** nel menu **Debug** .<br /><br /> Fare clic sul pulsante **Esegui istruzione/routine** sulla barra degli strumenti **Debug** .<br /><br /> Premere F10.|  
|Uscire da un modulo|Fare clic su **Esci da istruzione/routine** nel menu **Debug** .<br /><br /> Fare clic sul pulsante **Esci da istruzione/routine** sulla barra degli strumenti **Debug** .<br /><br /> Premere MAIUSC+F11.|  
|Eseguire il codice fino alla posizione corrente del cursore|Fare clic con il pulsante destro del mouse nella finestra dell'editor di query, quindi fare clic su **Esegui fino al cursore**.<br /><br /> Premere CTRL+F10.|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni del debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)  
  
  