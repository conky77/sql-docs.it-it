---
title: Usare la modalità RAW con FOR XML | Microsoft Docs
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML RAW mode
- XMLSCHEMA option
- FOR XML clause, RAW mode
- RAW FOR XML mode
- ELEMENTS directive
- RAW mode
- XMLDATA option
ms.assetid: 02c1bc0b-760c-4589-9ab1-6927c6d9c734
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: 7e88a1c65d2c8cdf8ba6129c8af28492dc362aba
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "75245242"
---
# <a name="use-raw-mode-with-for-xml"></a>Utilizzo della modalità RAW con FOR XML

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Nella modalità RAW ogni riga del set di risultati della query viene trasformata in un elemento XML al quale è assegnato l'identificatore generico \<row> o il nome di elemento specificato facoltativamente. Per impostazione predefinita, viene eseguito il mapping di ogni valore di colonna del set di righe diverso da NULL a un attributo dell'elemento \<row>. Se alla clausola FOR XML viene aggiunta la direttiva ELEMENTS, viene eseguito il mapping di ogni valore di colonna a un sottoelemento dell'elemento \<row>. Insieme alla direttiva ELEMENTS è possibile specificare facoltativamente l'opzione XSINIL per eseguire il mapping dei valori di colonna NULL del set di risultati a un elemento con l'attributo `xsi:nil="true"`.
  
 È possibile richiedere uno schema per il codice XML risultante. Se si specifica l'opzione XMLDATA, verrà restituito uno schema XDR inline. Se si specifica l'opzione XMLSCHEMA, verrà restituito uno schema XDS inline. che viene visualizzato all'inizio dei dati. Nel risultato, il riferimento allo spazio dei nomi dello schema viene ripetuto in ogni elemento di livello principale.  
  
 Per restituire i dati binari nel formato con codifica Base64, è necessario specificare l'opzione BINARY BASE64 nella clausola FOR XML. Se si recuperano dati binari nella modalità RAW senza specificare l'opzione BINARY BASE64, verrà generato un errore.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Questa sezione contiene gli esempi seguenti:  
  
-   [Esempio: recupero delle informazioni relative al modello del prodotto in formato XML](../../relational-databases/xml/example-retrieving-product-model-information-as-xml.md)  
  
-   [Esempio: specifica di XSINIL con la direttiva ELEMENTS](../../relational-databases/xml/example-specifying-xsinil-with-the-elements-directive.md)  
  
-   [Richiedere schemi come risultati con XMLDATA e XMLSCHEMA](../../relational-databases/xml/example-requesting-schemas-as-results-with-the-xmldata-and-xmlschema-options.md)  
  
-   [Esempio: recupero di dati binari](../../relational-databases/xml/example-retrieving-binary-data.md)  
  
-   [Esempio: ridenominazione dell'elemento &#60;row&#62;](../../relational-databases/xml/example-renaming-the-row-element.md)  
  
-   [Esempio: specifica di un elemento radice per codice XML generato da FOR XML](../../relational-databases/xml/example-specifying-a-root-element-for-the-xml-generated-by-for-xml.md)  
  
-   [Esempio: esecuzione di query sulle colonne di tipo XML](../../relational-databases/xml/example-querying-xmltype-columns.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Utilizzo della modalità AUTO con FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md)   
 [Utilizzo della modalità EXPLICIT con FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)   
 [Utilizzare la modalità PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md)
  
  
