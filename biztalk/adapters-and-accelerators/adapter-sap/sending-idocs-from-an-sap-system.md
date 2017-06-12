---
title: "Sending IDOCs from an SAP System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDOCs, sending"
  - "IDOCs, how to send"
ms.assetid: aea8a5e9-d775-4d52-a434-c2908b53cd2d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sending IDOCs from an SAP System
This section lists high-level tasks to be performed on the SAP system to send an IDOC from the SAP system to an external application. Each of these tasks in turn involves detailed procedures. Contact your SAP administrator for performing these tasks or see the SAP documentation.  
  
### To send an IDOC from an SAP system  
  
1.  Start the SAP GUI.  
  
2.  Create a logical system using BD54 transaction.  
  
3.  Create an RFC destination in TCP/IP connections using SM59 transaction.  
  
4.  Create a port using WE21 transaction and attach it to the RFC destination created in the last step.  
  
5.  Create a partner profile using WE20 transaction with the required message type and IDOC type, and then attach it to the port created in the last step.  
  
6.  Maintain a distributed model by connecting the message type to the port using the SALE transaction.  
  
7.  Generate an IDOC within SAP. For example, use BD10 transaction to trigger a MATMAS IDOC. Contact your SAP administrator for information about other transactions to trigger specific IDOCs.  
  
## See Also  
 [Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)