---
title: IRowsetFastLoad (OLE DB) | Microsoft Docs
description: IRowsetFastLoad (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 2d21e270eb7e2d387201d66df0bb566c3924d53c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2020
ms.locfileid: "67994402"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L'interfaccia **IRowsetFastLoad** espone il supporto per operazioni di copia bulk di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basate sulla memoria. I consumer di OLE DB Driver per SQL Server usano l'interfaccia per aggiungere rapidamente dati a una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esistente.  
  
 Se si imposta SSPROP_ENABLEFASTLOAD su VARIANT_TRUE per una sessione, non è possibile leggere dati dai set di righe restituiti successivamente dalla sessione. Quando SSPROP_ENABLEFASTLOAD è impostato su VARIANT_TRUE, tutti i set di righe creati nella sessione saranno del tipo IRowsetFastLoad. I set di righe IRowsetFastLoad non supportano la funzionalità di recupero del set di righe, quindi non è possibile leggere i set di righe.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRowsetFastLoad::Commit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md)|Contrassegna la fine di un batch di righe inserite e scrive le righe nella tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[IRowsetFastLoad::InsertRow &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|Aggiunge una riga al set di righe della copia bulk.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)   
 [Eseguire una copia bulk dei dati usando IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [Inviare dati BLOB a SQL Server usando IROWSETFASTLOAD e ISEQUENTIALSTREAM &#40;OLE DB&#41;](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
