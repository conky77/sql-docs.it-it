---
title: STPointFromText (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STPointFromText_TSQL
- STPointFromText (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STPointFromText (geometry Data Type)
ms.assetid: 1d71dfd8-9d80-44c3-b6e1-64e99cde1fa0
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: a198292700fdda1e5dc092afc4a5bb1948e7192a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "68075048"
---
# <a name="stpointfromtext-geometry-data-type"></a>STPointFromText (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un'istanza **geometry** da una rappresentazione WKT (Well-Known Text) OGC (Open Geospatial Consortium) integrata con qualsiasi valore Z (innalzamento) e M (misura) appartenente all'istanza.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STPointFromText ( 'point_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *point_tagged_text*  
 Rappresentazione WKT dell'istanza **geometryPoint** da restituire. *point_tagged_text* è un'espressione **nvarchar(max)** .  
  
 *SRID*  
 Espressione **int** che rappresenta l'identificatore SRID dell'istanza **geometryPoint** da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
 Tipo OGC: **Point**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genererà un'eccezione **FormatException** se l'input non è formattato in modo corretto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STPointFromText()` per creare un'istanza `geometry`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STPointFromText('POINT (100 100)', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

