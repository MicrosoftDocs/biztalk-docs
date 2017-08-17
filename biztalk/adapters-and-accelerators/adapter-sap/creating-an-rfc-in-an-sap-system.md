---
title: "Overview of creating an RFC in an SAP to use with the SAP adapter in BizTalk | Microsoft Docs"
description: Create an RFC, RFC destination, and send an RFC from SAP system - BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35937183-fc1e-49cd-8a75-8f62effe0013
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create and send an RFC in SAP
Lists high-level tasks to complete on the SAP system to create an RFC. Each task may involve very detailed procedures. As a result, we recommend contacting your SAP administrator to complete these tasks, or refer to the SAP guidance.  
  
## Create an RFC  
  
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

## Create an RFC destination  
  
1.  Start the SAP GUI.  
  
2.  Go to Transaction SM59 (Display and Maintain RFC Destinations).  
  
3.  From the menu bar, click **Create**.  
  
4.  Enter the RFC destination, connection type, description, and then press Enter.  
  
5.  Select the **Registered Server Program** radio-button, enter the program ID, gateway host, and gateway service.  
  
6.  Save the RFC destination.  

## Send an RFC from an SAP system  
  
1.  Start the SAP GUI.  
  
2.  Create a logical system using BD54 transaction.  
  
3.  Create an RFC destination in TCP/IP connections using SM59 transaction.  
  
4.  Create a port using WE21 transaction and attach it to the RFC destination created in the last step.  
  
5.  Trigger an RFC by using SE37. This RFC must contain the logic to make an RFC call to an external application and then receive a response from that application.  
  
## See Also  
 [Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)