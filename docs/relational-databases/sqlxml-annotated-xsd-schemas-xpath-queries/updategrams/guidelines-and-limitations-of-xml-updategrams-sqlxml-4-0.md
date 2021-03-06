---
title: Linee guida e limitazioni degli updategram (SQLXML)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9eb717968b191bb7d80f5d68542178bf32734b00
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "75241302"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Linee guida e limitazioni per gli updategram XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Quando si utilizzano updategram XML, tenere presenti le considerazioni seguenti:  
  
-   Se si utilizza un updategram per un'operazione di inserimento con una sola coppia di ** \<prima di>** e ** \<dopo>** blocchi, il ** \<blocco before>** può essere omesso. Viceversa, nel caso di un'operazione di eliminazione, il ** \<blocco after>** può essere omesso.  
  
-   Se si utilizza un updategram con più ** \<prima di>** e ** \<dopo>** blocchi nel tag di ** \<>di sincronizzazione** , è necessario specificare sia ** \<prima** dei blocchi>che ** \<dopo** i blocchi>per formare ** \<prima>** e **dopo \<** le coppie di>.  
  
-   Gli aggiornamenti in un updategram vengono applicati alla vista XML fornita da XML Schema. Ai fini della corretta esecuzione del mapping predefinito, è pertanto necessario specificare il nome del file dello schema nell'updategram o, se il nome di file non viene fornito, i nomi di elemento e di attributo devono corrispondere ai nomi di tabella e di colonna nel database.  
  
-   SQLXML 4.0 richiede che tutti i valori di colonna in un updategram vengano mappati in modo esplicito nello schema (XDR o XSD) fornito per creare la vista XML per i relativi elementi figlio. Questo comportamento è diverso rispetto alle versioni precedenti di SQLXML, che consentiva un valore per una colonna di cui non è stato eseguito il mapping nello schema se era implicito come parte della chiave esterna in un'annotazione **SQL: Relationship** . Si noti che questa modifica non influisce sulla propagazione dei valori di chiave primaria negli elementi figlio, che si verifica tuttora per SQLXML 4.0 se non viene specificato in modo esplicito alcun valore per l'elemento figlio.  
  
-   Se si utilizza un updategram per modificare i dati in una colonna binaria, ad esempio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] il tipo di dati **Image** , è necessario specificare uno schema di mapping in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cui è necessario specificare il tipo di dati (ad esempio, **SQL: DataType = "image"**) e il tipo di dati XML (ad esempio, **DT: Type = "BinHex"** o **DT: Type = "binbase64**). I dati per la colonna binaria devono essere specificati nell'updategram. l'annotazione **SQL: URL-encode** specificata nello schema di mapping viene ignorata dall'updategram.  
  
-   Quando si scrive uno schema XSD, se il valore specificato per l'annotazione **SQL: relation** o **SQL: Field** include un carattere speciale, ad esempio uno spazio (ad esempio, nel nome della tabella "Order Details"), questo valore deve essere racchiuso tra parentesi quadre, ad esempio "[Order Details]".  
  
-   Quando si utilizzano updategram, le relazioni a catena non sono supportate. Se, ad esempio, le tabelle A e C sono correlate tramite una relazione a catena che utilizza la tabella B, si verifica l'errore seguente quando si tenta di eseguire l'updategram:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Anche se lo schema e l'updategram sono entrambi altrimenti corretti e hanno un formato valido, l'errore si verifica se è presente una relazione a catena.  
  
-   Gli updategram non consentono il passaggio dei dati del tipo di **immagine** come parametri durante gli aggiornamenti.  
  
-   **I \<** tipi BLOB (Binary Large Object) come **text/ntext** e images non devono essere utilizzati nel blocco before>in quando si utilizzano updategram, perché verranno inclusi per l'utilizzo nel controllo della concorrenza. Ciò può provocare problemi con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a causa delle limitazioni applicate al confronto per i tipi BLOB. La parola chiave LIKE, ad esempio, viene utilizzata nella clausola WHERE per il confronto tra colonne con tipo di dati **Text** . Tuttavia, i confronti avranno esito negativo in caso di tipi BLOB in cui le dimensioni dei dati sono maggiori di 8K.  
  
-   I caratteri speciali nei dati **ntext** possono causare problemi con SQLXML 4,0 a causa delle limitazioni del confronto per i tipi di BLOB. Ad esempio, l'utilizzo di "[Serializable]" nel blocco ** \<before>** di uno updategram se utilizzato nel controllo della concorrenza di una colonna di tipo **ntext** avrà esito negativo con la descrizione dell'errore SQLOLEDB seguente:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulla sicurezza degli updategram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
