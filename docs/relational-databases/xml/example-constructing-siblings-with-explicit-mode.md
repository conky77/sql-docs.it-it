---
title: 'Esempio: creazione di elementi di pari livello con la modalità EXPLICIT | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- EXPLICIT FOR XML mode
ms.assetid: 8a57b765-a890-46a3-8b5f-5754e921ea6e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 606c83c59147bf6ef171d4fa4f802d13f55f8219
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68006828"
---
# <a name="example-constructing-siblings-with-explicit-mode"></a>Esempio: Creazione di elementi di pari livello utilizzando la modalità EXPLICIT
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Si supponga di voler creare codice XML per fornire informazioni sugli ordini di vendita. <`SalesPerson`> e <`OrderDetail`> sono elementi di pari livello. Ogni ordine dispone di un elemento <`OrderHeader`>, un elemento <`SalesPerson`> e uno o più elementi <`OrderDetail`>.  
  
```  
<OrderHeader SalesOrderID=... OrderDate=... CustomerID=... >  
  <SalesPerson SalesPersonID=... />  
  <OrderDetail SalesOrderID=... LineTotal=... ProductID=... OrderQty=... />  
  <OrderDetail SalesOrderID=... LineTotal=... ProductID=... OrderQty=.../>  
      ...  
</OrderHeader>  
<OrderHeader ...</OrderHeader>  
```  
  
 La query in modalità EXPLICIT genera questo codice XML. La query specifica valori di `Tag` pari a 1 per l'elemento <`OrderHeader`>, pari a 2 per l'elemento <`SalesPerson`> e pari a 3 per l'elemento <`OrderDetail`>. Poiché <`SalesPerson`> e <`OrderDetail`> sono elementi di pari livello, la query specifica lo stesso valore di tag `Parent` pari a 1 per l'identificazione dell'elemento <`OrderHeader`>.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        SalesOrderID  as [OrderHeader!1!SalesOrderID],  
        OrderDate     as [OrderHeader!1!OrderDate],  
        CustomerID    as [OrderHeader!1!CustomerID],  
        NULL          as [SalesPerson!2!SalesPersonID],  
        NULL          as [OrderDetail!3!SalesOrderID],  
        NULL          as [OrderDetail!3!LineTotal],  
        NULL          as [OrderDetail!3!ProductID],  
        NULL          as [OrderDetail!3!OrderQty]  
FROM   Sales.SalesOrderHeader  
WHERE     SalesOrderID=43659 or SalesOrderID=43661  
UNION ALL   
SELECT 2 as Tag,  
       1 as Parent,  
        SalesOrderID,  
        NULL,  
        NULL,  
        SalesPersonID,    
        NULL,           
        NULL,           
        NULL,  
        NULL           
FROM   Sales.SalesOrderHeader  
WHERE     SalesOrderID=43659 or SalesOrderID=43661  
UNION ALL  
SELECT 3 as Tag,  
       1 as Parent,  
        SOD.SalesOrderID,  
        NULL,  
        NULL,  
        SalesPersonID,  
        SOH.SalesOrderID,  
        LineTotal,  
        ProductID,  
        OrderQty     
FROM    Sales.SalesOrderHeader SOH,Sales.SalesOrderDetail SOD  
WHERE   SOH.SalesOrderID = SOD.SalesOrderID  
AND     (SOH.SalesOrderID=43659 or SOH.SalesOrderID=43661)  
ORDER BY [OrderHeader!1!SalesOrderID], [SalesPerson!2!SalesPersonID],  
         [OrderDetail!3!SalesOrderID],[OrderDetail!3!LineTotal]  
FOR XML EXPLICIT;  
```  
  
 Risultato parziale:  
  
```
<OrderHeader SalesOrderID="43659" OrderDate="2005-07-01T00:00:00" CustomerID="676">
  <SalesPerson SalesPersonID="279" />
  <OrderDetail SalesOrderID="43659" LineTotal="10.373000" ProductID="712" OrderQty="2" />
  <OrderDetail SalesOrderID="43659" LineTotal="28.840400" ProductID="716" OrderQty="1" />
  <OrderDetail SalesOrderID="43659" LineTotal="34.200000" ProductID="709" OrderQty="6" />
    ...
</OrderHeader>
<OrderHeader SalesOrderID="43661" OrderDate="2005-07-01T00:00:00" CustomerID="442">
  <SalesPerson SalesPersonID="282" />
  <OrderDetail SalesOrderID="43661" LineTotal="20.746000" ProductID="712" OrderQty="4" />
  <OrderDetail SalesOrderID="43661" LineTotal="40.373000" ProductID="711" OrderQty="2" />
  ...
</OrderHeader>
```
  
## <a name="see-also"></a>Vedere anche  
 [Usare la modalità EXPLICIT con FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
