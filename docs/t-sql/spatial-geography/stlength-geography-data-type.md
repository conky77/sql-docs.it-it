---
title: STLength (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STLength (geography Data Type)
- STLength_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STLength method
ms.assetid: 774560ab-4a4a-4058-b043-1e67cf6fb9eb
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 61487b976322f8725f9398e54f8292919ff0ca58
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68139113"
---
# <a name="stlength-geography-data-type"></a>STLength (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce la lunghezza totale degli elementi in un'istanza **geography** o le istanze **geography** in una **GeometryCollection**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STLength ( )  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **float**  
  
 Tipo CLR restituito: **SqlDouble**  
  
## <a name="remarks"></a>Osservazioni  
 Se un'istanza **geography** è chiusa, la lunghezza viene calcolata come lunghezza totale lungo l'istanza. La lunghezza di qualsiasi poligono è il relativo perimetro e la lunghezza di un punto è 0. La lunghezza di un oggetto **GeometryCollection** viene calcolata eseguendo la somma delle lunghezze di tutte le istanze **geography** contenute nella raccolta.  
  
 STLength() può essere utilizzato con oggetti LineString validi e non validi. In genere, un oggetto LineString non è valido a causa di segmenti sovrapposti dovuti ad anomalie, ad esempio tracce GPS imprecise. STLength() non rimuove i segmenti sovrapposti o non validi, i quali vengono inclusi nel valore di lunghezza restituito. È possibile rimuovere i segmenti sovrapposti da un oggetto LineString con il metodo MakeValid().  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato `STLength()` per trovare la lunghezza dell'istanza.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STLength();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
