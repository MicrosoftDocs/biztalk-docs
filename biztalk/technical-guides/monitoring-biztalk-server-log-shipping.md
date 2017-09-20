---
title: "Monitoring BizTalk Server Log Shipping | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fae4ff40-7d86-4e9b-b1cc-4f00486ae4b9
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring BizTalk Server Log Shipping
To determine the last successful backup set of BizTalk Server databases and logs that have been restored, review the contents of the Master.dbo.bts_LogShippingHistory table on the destination [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s). This table is populated by the BizTalk Server Log Shipping Get Backup History job and is updated by the restore job. When a backup is successfully restored, the Restored column is set to a value of 1 and the RestoredDateTime is set to the current date and time.  
  
 When all of the databases restored to the server from a particular backup set listed in the Master.dbo.bts_LogShippingHistory table have been successfully restored, the backup set ID is written to the Master.dbo.bts_LogShippingLastRestoreSet table. This table stores the last set restored and is useful for determining what backup set of logs need to be restored to bring the destination BizTalk group online after the occurrence of a disaster recovery event.  
  
## See Also  
 [Configuring BizTalk Server Log Shipping](../technical-guides/configuring-biztalk-server-log-shipping.md)