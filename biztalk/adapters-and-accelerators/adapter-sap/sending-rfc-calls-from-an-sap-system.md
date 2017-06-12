---
title: "Sending RFC Calls from an SAP System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RFC, sending calls"
  - "RFC, how to send RFC calls"
ms.assetid: e41b2b22-4171-4102-8ea1-73170b2e2efc
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sending RFC Calls from an SAP System
This section lists high-level tasks to be performed on the SAP system to send an RFC call from the SAP system to an external application. Each of these tasks in turn involves detailed procedures. You must contact your SAP administrator for performing these tasks or refer to SAP documentation.  
  
### To send an RFC from an SAP system  
  
1.  Start the SAP GUI.  
  
2.  Create a logical system using BD54 transaction.  
  
3.  Create an RFC destination in TCP/IP connections using SM59 transaction.  
  
4.  Create a port using WE21 transaction and attach it to the RFC destination created in the last step.  
  
5.  Trigger an RFC by using SE37. This RFC must contain the logic to make an RFC call to an external application and then receive a response from that application.  
  
## See Also  
 [Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios](../../adapters-and-accelerators/adapter-sap/performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)