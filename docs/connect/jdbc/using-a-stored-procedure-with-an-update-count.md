---
title: Uso di una stored procedure con i conteggi di aggiornamento | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 851974955b9311efc149ecdff310bfbb1d8869fc
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026933"
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>Uso di una stored procedure con i conteggi di aggiornamento

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Per modificare i dati in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando una stored procedure, in [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] è disponibile la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Mediante la classe SQLServerCallableStatement è possibile chiamare le stored procedure che consentono di modificare i dati nel database e restituire un conteggio del numero di righe interessate, noto anche come conteggio aggiornamenti.

Dopo aver impostato la chiamata alla stored procedure usando la classe SQLServerCallableStatement, chiamare la stored procedure usando il metodo [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) o il metodo [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md). Il metodo executeUpdate restituisce un valore **int** contenente il numero di righe interessate dalla stored procedure, diversamente dal metodo execute. Se si usa il metodo execute e si desidera ottenere il conteggio del numero di righe interessate, chiamare il metodo [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) dopo avere eseguito la stored procedure.

> [!NOTE]  
> Se si desidera che il driver JDBC restituisca tutti i conteggi degli aggiornamenti, inclusi i conteggi degli aggiornamenti restituiti dai trigger eventualmente attivati, impostare la proprietà della stringa di connessione lastUpdateCount su "false". Per altre informazioni sulla proprietà lastUpdateCount, vedere [Impostazione delle proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).

Come esempio viene creata la tabella e la stored procedure seguenti e vengono inseriti i dati di esempio nel database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:

```sql
CREATE TABLE TestTable
   (Col1 int IDENTITY,
    Col2 varchar(50),
    Col3 int);  

CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```

Nell'esempio seguente viene passata alla funzione una connessione aperta al database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], il metodo execute viene usato per la chiamata alla stored procedure UpdateTestTable, quindi viene usato il metodo getUpdateCount per restituire un conteggio delle righe interessate dalla stored procedure.

[!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]

## <a name="see-also"></a>Vedere anche

[Uso delle istruzioni con le stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)
