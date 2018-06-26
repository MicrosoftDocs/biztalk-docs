---
title: "Step 3: Test the Migrated Application5 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "migration, testing the migrated application (Receive IDOC)"
  - "migration"
ms.assetid: 3ad15069-1556-4c0a-8bfd-86704d40c586
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Test the Migrated Application
![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you will test the migrated application by receiving a flat-file IDOC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## Prerequisites  
  
- Configure the BizTalk application by mapping the logical ports in the BizTalk orchestration to physical ports in the BizTalk Server Administration console.  
  
- Configure the BizTalk application to use the WCF-Custom receive port for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### To test the migrated application  
  
1.  Start the SAP GUI, and connect to the SAP system that you specified in the connection URI.  
  
2.  Run SE37, and invoke a function module in SAP that sends an IDOC to an external system. Make sure you send the IDOC using the same program ID that is specified in the connection URI for the WCF-Custom receive port.  
  
3.  Look for the inbound IDOC at the file location specified as part of the orchestration.  
  
## See Also  
 [Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)