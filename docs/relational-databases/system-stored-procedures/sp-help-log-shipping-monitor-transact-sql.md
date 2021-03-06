---
title: sp_help_log_shipping_monitor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_TSQL
- sp_help_log_shipping_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor
ms.assetid: a4e96c45-6dcd-471a-a494-b5c619459855
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2b8fc2ac96821427aaf0ef2550fb6624a923d7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68000936"
---
# <a name="sp_help_log_shipping_monitor-transact-sql"></a>sp_help_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un set di risultati contenente lo stato e altre informazioni per i database primari e secondari registrati in un server primario, secondario o di monitoraggio.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_log_shipping_monitor  
```  
  
## <a name="arguments"></a>Argomenti  
 No.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**status**|**bit**|Stato collettivo degli agenti per il database per il log shipping:<br /><br /> **0** = errori integri e senza agente.<br /><br /> **1** = in caso contrario.|  
|**is_primary**|**bit**|Indica se questa riga è per un database primario o meno:<br /><br /> **1** = la riga è per un database primario.<br /><br /> **0** = la riga è per un database secondario.|  
|**Server**|**sysname**|Nome del server primario o secondario contenente il database.|  
|**database_name**|**sysname**|Nome del database.|  
|**time_since_last_backup**|**int**|Periodo di tempo, in minuti, dall'ultimo backup del log.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.|  
|**last_backup_file**|**nvarchar (500)**|Nome dell'ultimo file di backup del log.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.|  
|**backup_threshold**|**int**|Periodo di tempo, in minuti, dall'ultimo backup trascorso il quale viene generato un errore threshold_alert. **backup_threshold** è di **tipo int**e il valore predefinito è **60 minuti**.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.<br /><br /> Questo valore può essere modificato utilizzando [sp_add_log_shipping_primary_database &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md).|  
|**is_backup_alert_enabled**|**bit**|Specifica se verrà generato un avviso quando viene superato **backup_threshold** . Il valore**1 (1**), ovvero il valore predefinito, indica che verrà generato l'avviso.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.<br /><br /> Questo valore può essere modificato utilizzando [sp_add_log_shipping_primary_database &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md).|  
|**time_since_last_copy**|**int**|Periodo di tempo, in minuti, dall'ultima copia del backup del log.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.|  
|**last_copied_file**|**nvarchar (500)**|Nome dell'ultimo file di backup del log copiato.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.|  
|**time_since_last_restore**|**int**|Periodo di tempo, in minuti, dall'ultimo ripristino del backup del log.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.|  
|**last_restored_file**|**nvarchar (500).**|Nome dell'ultimo file di backup del log ripristinato.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.|  
|**last_restored_latency**|**int**|Periodo di tempo, in minuti, dalla creazione dell'ultimo backup al ripristino del backup.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.|  
|**restore_threshold**|**int**|Numero di minuti che può trascorrere tra operazioni di ripristino prima che venga generato un avviso. **restore_threshold** non può essere null.|  
|**is_restore_alert_enabled**|**bit**|Specifica se viene generato un avviso quando viene superato **restore_threshold** . Il valore**1 (1**), ovvero il valore predefinito, indica che l'avviso viene generato.<br /><br /> NULL = Informazioni non disponibili o non rilevanti.<br /><br /> Per impostare la soglia di ripristino, utilizzare [sp_add_log_shipping_secondary_database](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md).|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_log_shipping_monitor** deve essere eseguito dal database **Master** sul server di monitoraggio.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul log shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
