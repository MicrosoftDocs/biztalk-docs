---
title: "Send IDOCs from an SAP system to use the mySAP adapter in BizTalk | Microsoft Docs"
description: Send IDOCs, view transaction IDs, and view details about sent IDOCs - BizTalk Adapter Pack (BAP)
description: 
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aea8a5e9-d775-4d52-a434-c2908b53cd2d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sending IDOCs from an SAP System
High-level tasks to complete on the SAP system to send an IDOC from the SAP system to an external application. Contact your SAP administrator for performing these tasks or see the SAP guidance.  
  
## Send an IDOC from SAP  
  
1.  Start the SAP GUI.  
  
2.  Create a logical system using BD54 transaction.  
  
3.  Create an RFC destination in TCP/IP connections using SM59 transaction.  
  
4.  Create a port using WE21 transaction and attach it to the RFC destination created in the last step.  
  
5.  Create a partner profile using WE20 transaction with the required message type and IDOC type, and then attach it to the port created in the last step.  
  
6.  Maintain a distributed model by connecting the message type to the port using the SALE transaction.  
  
7.  Generate an IDOC within SAP. For example, use BD10 transaction to trigger a MATMAS IDOC. Contact your SAP administrator for information about other transactions to trigger specific IDOCs.  

## View Transaction IDs in SAP
When the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] invokes a tRFC or sends an IDOC to an SAP system, the SAP system registers a transaction ID (TID) in response. In some scenarios, you might need to know the TID that is registered with the SAP system in response to a call from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. For example, you might want to identify the logical unit of work (LUW) on the SAP system to troubleshoot an issue.  
  
 To view the TIDs in an SAP system, you must use transaction SM58. Contact your SAP administrator or refer to the SAP guidance for more information about this transaction. 

## View details about IDOCs sent and received from SAP
Using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you can send an IDOC to an SAP system or receive an IDOC from an SAP system. To track the status and view the data of an IDOC sent or received by an SAP system, you can use transaction WE02. Contact your SAP administrator, or refer to the SAP guidance for more information about this transaction.  

  
## See Also  
 [Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)