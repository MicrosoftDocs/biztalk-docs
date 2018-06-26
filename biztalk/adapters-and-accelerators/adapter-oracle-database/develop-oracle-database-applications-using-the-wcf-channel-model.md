---
title: "Develop Oracle Database applications using the WCF Channel Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF channel model, streaming"
  - "channel programming, streaming"
  - "WCF channel model, performing operations"
  - "developing applications, by using the WCF channel model"
  - "streaming, using the WCF channel model"
  - "WCF channel model, developingn applications"
  - "channel programming, performing operations"
ms.assetid: cb6bf5fd-ff90-44bd-a9dd-03b00f12a78d
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop Oracle Database applications using the WCF Channel Model
You can use the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] channel model to consume the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] by sending XML messages directly over a channel instance created with the Oracle DB Binding.  
  
 One advantage of using the WCF channel model over using the strongly-typed classes and methods that the WCF service model exposes is that the channel model provides more fine-grained control over the operations that you perform on the Oracle database. Why? In the WCF channel model you directly control the contents of the messages that you send over the channel.  
  
 In certain scenarios, this extra level of control can be beneficial. For example, when you use the WCF channel model to perform an Update operation on a table, you can selectively update columns in the target rows by omitting columns from the update template that you pass in the message. The update method exposed by a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] client uses a strongly-typed record parameter for the template that includes every column in the table schema. If a column has “nillable=false” in the WSDL, it must be updated using the WCF service model.  
  
 Another key advantage that the WCF channel model provides over the WCF service model is more comprehensive support for end-to-end streaming of Oracle large object (LOB) data types. By using the WCF channel model you can perform end-to-end streaming:  
  
- To update an LOB column in a table or view using the UpdateLOB operation.  
  
- On OUT and IN OUT parameters containing LOB data that are returned by procedures and functions.  
  
- On LOB data that is contained in the result of a SQLEXECUTE operation.  
  
- On LOB data columns that are returned in the POLLINGSTMT operation.  
  
- On LOB data columns that are returned by a Select operation on a table or view.  
  
  This is because in the WCF channel model you directly control how you provide the message body on outgoing messages and how you process the message body on incoming messages.  
  
  In contrast, the WCF service model only provides:  
  
- End-to-end streaming for LOB data on one operation, the ReadLOB operation.  
  
- No capability to update LOB data on the Oracle database in a streamed fashion.  
  
  The sections in this topic explain how to perform operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using the WCF channel model.  
  
## In This Section  
  
-   [Overview of the WCF channel model with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-channel-model-with-the-oracle-database-adapter.md) 
  
-   [Create a channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) 
  
-   [Invoke Operations on the Oracle Database Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-operations-on-the-oracle-database-using-the-wcf-channel-model.md)  
  
-   [Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [Run an Insert Operation in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [Invoke a Function in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [Receive Polling-based Data-changed Messages in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)  
  
-   [Streaming Oracle Database LOB Data Types Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)