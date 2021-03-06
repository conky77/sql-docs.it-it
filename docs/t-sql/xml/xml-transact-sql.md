---
title: xml (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d8d863a6ca6a44a323c05f26298c68de774dfc3b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "67948024"
---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Tipo di dati in cui vengono archiviati i dati XML. È possibile archiviare istanze **xml** in una colonna oppure una variabile di tipo **xml**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
## <a name="arguments"></a>Argomenti  
 CONTENT  
 Limita l'istanza **xml** a un frammento XML in formato corretto. I dati XML possono contenere più 0 (zero) o più elementi al livello principale. Al livello principale sono inoltre consentiti nodi di testo.  
  
 Questo è il comportamento predefinito.  
  
 DOCUMENT  
 Limita l'istanza **xml** a un documento XML in formato corretto. I dati XML devono disporre di un unico elemento radice. Al livello principale non sono consentiti nodi di testo.  
  
 *xml_schema_collection*  
 Nome di una raccolta di XML Schema. Per creare una colonna o una variabile **xml** tipizzata, facoltativamente è possibile specificare il nome della raccolta di XML Schema. Per altre informazioni sul codice XML tipizzato e non tipizzato, vedere [Confrontare dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="remarks"></a>Osservazioni  
 Le dimensioni della rappresentazione archiviata delle istanze del tipo di dati **xml** non possono superare 2 gigabyte (GB).  
  
 I facet CONTENT e DOCUMENT sono applicabili soltanto a XML tipizzato. Per altre informazioni, vedere [Confrontare dati XML tipizzati con dati XML non tipizzati](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="examples"></a>Esempi  
  
```  
USE AdventureWorks;  
GO  
DECLARE @DemographicData xml (Person.IndividualSurveySchemaCollection);  
SET @DemographicData =  (SELECT TOP 1 Demographics FROM Person.Person);  
SELECT @DemographicData;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Conversione di tipi di dati &#40;motore di database&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [metodi con tipo di dati XML](../../t-sql/xml/xml-data-type-methods.md)   
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
