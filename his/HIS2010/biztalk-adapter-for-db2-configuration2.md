---
title: "BizTalk Adapter for DB2 Configuration2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 689f2b31-b4a4-4071-abdd-8c26806f1a4f
caps.latest.revision: 5
---
# BizTalk Adapter for DB2 Configuration
The BizTalk Adapter for DB2 is a send and receive adapter that enables BizTalk orchestrations to interact with host systems. Specifically, the adapter enables send and receive operations over TCP/IP and APPC connections to DB2 databases running on mainframe, AS/400, and UDB platforms. Based on Host Integration Server technology, the adapter uses the Data Access Library to configure DB2 connections, and the Managed Provider for DB2 to issue SQL commands and stored procedures.  
  
 The adapter serves two main functions:  
  
-   For **Send** operations (both One Way and Solicit Response), the adapter sends SQL commands and stored procedures to a DB2 instance, with the option of soliciting a response.  
  
-   For **Receive** operations (One Way only), the adapter creates an SQL command or stored procedure that polls DB2 objects and creates per-row messages, which are then submitted to the BizTalk message system.  
  
 In addition, the BizTalk Adapter for DB2 uses the standard BizTalk Adapter tracing tool as a troubleshooting mechanism.  
  
## In This Section  
 [How to Create a Send Port for the DB2 Adapter](../HIS2010/how-to-create-a-send-port-for-the-db2-adapter1.md)  
  
 [How to Create a Receive Port and a Receive Location for the Host File Adapter](../HIS2010/how-to-create-a-receive-port-and-a-receive-location-for-the-host-file-adapter1.md)  
  
 [How to Create a Schema for the DB2 Adapter](../HIS2010/how-to-create-a-schema-for-the-db2-adapter1.md)  
  
 [Creating a BizTalk Application with the DB2 Adapter](../HIS2010/creating-a-biztalk-application-with-the-db2-adapter.md)  
  
## See Also  
 [Managed Provider for DB2](../HIS2010/managed-provider-for-db22.md)