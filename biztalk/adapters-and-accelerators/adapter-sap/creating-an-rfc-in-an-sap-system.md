---
title: "Creating an RFC in an SAP System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RFC, how to create"
  - "RFC, creating"
ms.assetid: 35937183-fc1e-49cd-8a75-8f62effe0013
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating an RFC in an SAP System
This section lists high-level tasks to be performed on the SAP system to create an RFC. Each of these tasks in turn involves detailed procedures. You must contact your SAP administrator for performing these tasks or refer to the SAP documentation.  
  
### To create an RFC  
  
1.  Start the SAP GUI.  
  
2.  Go to Transaction SE37 (Function Builder), enter the RFC name, and click **Create**.  
  
3.  Enter an existing function group under which the RFC will be created, a short description for the RFC, and click **Save**.  
  
4.  In the **Attributes** tab, select the **Remote-Enabled Module** radio button.  
  
5.  In the **Import** tab, enter the import parameters. These parameters are used for passing the external data to the function module.  
  
6.  In the **Export** tab, enter the export parameters.  
  
7.  In the **Changing** tab, enter the changing parameters.  
  
8.  In the **Tables** tab, enter the table names.  
  
9. In the **Exceptions** tab, enter the exceptions to handle errors.  
  
10. In the **Source Code** tab, enter the source code (logic) for the RFC.  
  
11. Click the **Activate** icon on the toolbar to activate the function module.  
  
## See Also  
 [Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)