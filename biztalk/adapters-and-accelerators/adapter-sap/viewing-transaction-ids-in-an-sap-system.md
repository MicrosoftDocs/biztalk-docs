---
title: "Viewing Transaction IDs in an SAP System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "logical unit of work"
  - "transaction IDs, viewing in an SAP system"
  - "TID"
  - "LUW"
ms.assetid: ef457839-2544-4f07-9266-4a0b2450e1e5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Viewing Transaction IDs in an SAP System
When the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] invokes a tRFC or sends an IDOC to an SAP system, the SAP system registers a transaction ID (TID) in response. In some scenarios, you might need to know the TID that is registered with the SAP system in response to a call from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. For example, you might want to identify the logical unit of work (LUW) on the SAP system to troubleshoot an issue.  
  
 To view the TIDs in an SAP system, you must use transaction SM58. For more information about this transaction, contact your SAP administrator or refer to the SAP documentation.  
  
## See Also  
 [Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)