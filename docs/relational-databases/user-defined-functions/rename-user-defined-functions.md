---
title: Rinominare funzioni definite dall'utente | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 274c79dabe90098094423b2994edb93603e649e1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68123567"
---
# <a name="rename-user-defined-functions"></a>Ridenominare funzioni definite dall'utente
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
  È possibile rinominare funzioni definite dall'utente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Rinominare funzioni definite dall'utente tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   I nomi di funzione devono essere conformi alla regole per gli [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
-   La ridenominazione di una funzione definita dall'utente non comporta la modifica del nome dell'oggetto corrispondente nella colonna di definizione della vista del catalogo **sys.sql_modules** . È pertanto consigliabile evitare di rinominare questo tipo di oggetto. In alternativa, eliminare e ricreare la stored procedure con il nuovo nome.  
  
-   La modifica del nome o della definizione di una funzione definita dall'utente può provocare errori degli oggetti dipendenti se questi non vengono aggiornati in base alla modifica apportata alla funzione.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per eliminare la funzione, è necessaria l'autorizzazione ALTER per lo schema a cui appartiene la funzione o l'autorizzazione CONTROL per la funzione. Per ricreare la funzione, sono necessarie l'autorizzazione CREATE FUNCTION per il database e l'autorizzazione ALTER per lo schema in cui viene creata la funzione.  
  
##  <a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-rename-user-defined-functions"></a>Per rinominare funzioni definite dall'utente  
  
1.  In **Esplora oggetti**fare clic sul segno più accanto al database che contiene la funzione che si desidera rinominare.  
  
2.  Fare clic sul segno più accanto alla cartella **Programmabilità** .  
  
3.  Fare clic sul segno più accanto alla cartella che contiene la funzione che si desidera rinominare:  
  
    -   Table-valued Function  
  
    -   Funzione a valori scalari  
  
    -   Funzione di aggregazione  
  
4.  Fare clic con il pulsante destro del mouse sulla funzione da rinominare e scegliere **Rinomina**.  
  
5.  Immettere il nuovo nome della funzione.  
  
##  <a name="TsqlProcedure"></a> Con Transact-SQL  
 **Per rinominare funzioni definite dall'utente**  
  
 Non è possibile eseguire questa attività utilizzando istruzioni Transact-SQL. Per rinominare una funzione definita dall'utente tramite Transact-SQL, è innanzitutto necessario eliminare la funzione esistente e quindi ricrearla con il nuovo nome. Assicurarsi che tutto il codice e tutte le applicazioni in cui è stato usato il nome precedente della funzione usino ora il nuovo nome.  
  
 Per altre informazioni, vedere [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md) e [DROP FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-function-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [Visualizzare funzioni definite dall'utente](../../relational-databases/user-defined-functions/view-user-defined-functions.md)  
  
  
