---
title: riferimento mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Articolo di riferimento per i comandi mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d15b4149fe336b173452030ec67fb7f229e6ae3d
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527284"
---
# <a name="mssqlctl"></a>mssqlctl

L'articolo seguente fornisce informazioni di riferimento per la **mssqlctl** dello strumento per [cluster di big data 2019 Server SQL (anteprima)](big-data-cluster-overview.md). Per altre informazioni su come installare il **mssqlctl** dello strumento, vedere [installare mssqlctl per gestire i cluster di big data di SQL Server 2019](deploy-install-mssqlctl.md).

## <a id="commands"></a> Comandi

|||
|---|---|
| [app](reference-mssqlctl-app.md) | Creare, eliminare, eseguire e gestire le applicazioni. |
| [cluster](reference-mssqlctl-cluster.md) | Selezionare, gestire e operare i cluster. |
| [login](#login) | Accedere al cluster. |
| [logout](#logout) | Disconnettersi dal cluster. |
| [storage](reference-mssqlctl-storage.md) | Gestire l'archiviazione del cluster. |

## <a id="login"></a> account di accesso mssqlctl

Accedere al cluster.

```
mssqlctl login
   --endpoint
   --password
   --username
```

### <a name="parameters"></a>Parametri

| Parametro | Descrizione |
|---|---|
|**--endpoint -e**| Cluster host e porta (ex) `http://host:port"`. |
|**--password -p**| Credenziali password. |
|**-- username -u**| Account utente. |

### <a name="examples"></a>Esempi

Accedere in modo interattivo.

```
mssqlctl login
```

Accedere con nome utente e password.

```
mssqlctl login -u johndoe@contoso.com -p VerySecret
```

Accedere con l'endpoint del cluster, nome utente e password.

```
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```

## <a id="logout"></a> disconnessione mssqlctl

Disconnettersi dal cluster.

```
mssqlctl logout
   --username
```

### <a name="parameters"></a>Parametri

| Parametri | Descrizione |
|---|---|
| **-- username -u** | Account utente, se mancanti, disconnessione, l'account attivo corrente. |

### <a name="examples"></a>Esempi

Disconnettere l'utente.

```
mssqlctl logout --username admin
```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come installare il **mssqlctl** dello strumento, vedere [installare mssqlctl per gestire i cluster di big data di SQL Server 2019](deploy-install-mssqlctl.md).