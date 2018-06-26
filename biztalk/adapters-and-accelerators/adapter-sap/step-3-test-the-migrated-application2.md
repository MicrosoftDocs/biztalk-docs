---
title: "Step 3: Test the Migrated Application2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "migration, testing the migrated application (Send IDOC)"
  - "migration"
ms.assetid: 8dc0d127-71ce-4668-a3bf-c893a8f6848d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Test the Migrated Application
![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you will test the migrated application by sending a flat-file IDOC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## Prerequisites  
  
- Configure the BizTalk application by mapping the logical ports in the BizTalk orchestration to physical ports in the BizTalk Server Administration console.  
  
- Configure the BizTalk application to use the WCF-custom send port for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### To test the migrated application  
  
1.  From the SendIDOC_Migration folder, copy the BOMDOC.txt file. This is the flat-file IDOC to be sent to the SAP system.  
  
2.  Paste the flat-file IDOC to the folder that is mapped to the file receive location.  
  
3.  The orchestration consumes the file and sends the IDOC to the SAP system. Verify if there are any errors in the event viewer.  
  
## See Also  
 [Tutorial 3: Migrating an SAP Send IDOC BizTalk Project](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)