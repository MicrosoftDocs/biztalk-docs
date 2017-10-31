---
title: "BizTalk Adapter for DB2 Configuration1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9bbbaa5-a07a-491b-8539-3f6e5b257466
caps.latest.revision: 5
---
# BizTalk Adapter for DB2 Configuration
The Microsoft BizTalk Adapter for DB2 connects BizTalk Server 2013 to vital data stored in IBM mainframe DB2 for z/OS, IBM midrange DB2 for i5/OS, and IBM server DB2 running on Linux, UNIX and Windows operating systems. The adapter is based on the Microsoft ADO.NET Data Provider for DB2 and supports a broad range of functions, including send ports and receive ports with distributed transactions across SNA and TCP/IP network connections. Using SQL commands defined within port configuration wizards, IT professionals can easily create solutions that efficiently integrate DB2 databases without writing code.  
  
 The adapter serves two main functions:  
  
-   For **Send** operations (both One Way and Solicit Response), the adapter sends SQL commands and stored procedures to a DB2 instance, with the option of soliciting a response.  
  
-   For **Receive** operations (One Way only), the adapter creates an SQL command or stored procedure that polls DB2 objects and creates per-row messages, which are then submitted to the BizTalk message system.  
  
 In addition, the BizTalk Adapter for DB2 uses the standard BizTalk Adapter tracing tool as a troubleshooting mechanism.  
  
## In This Section  
 [How to Create a Send Port for the DB2 Adapter](../core/how-to-create-a-send-port-for-the-db2-adapter.md)  
  
 [How to Create a Receive Port and a Receive Location for the Host File Adapter](../core/how-to-create-a-receive-port-and-a-receive-location-for-the-host-file-adapter.md)  
  
 [How to Create a Schema for the DB2 Adapter](../core/how-to-create-a-schema-for-the-db2-adapter.md)