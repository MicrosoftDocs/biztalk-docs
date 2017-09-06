---
title: "Message Schemas for the Polling and TypedPolling Operations for the SQL adapter in BizTalk | Microsoft Docs"
description: Polling and TypedPolling message structure used by the SQL adapter in BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e900307-2c9c-493b-81c9-67af3e143eeb
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for the Polling and TypedPolling Operations
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces the Polling and TypedPolling inbound operations to return the result set of the polling query to an adapter client.  
  
 You configure the Polling and TypedPolling operations by setting binding properties in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. For more information about these binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). You set the **PollingStatement** binding property to specify a SQL statement (SELECT or EXEC \<stored procedure>) for the polling query. The result set of this query is returned as data to your code in the Polling operation, and as strongly-typed data in the TypedPolling operation. The structure of the result set is determined by the metadata that the adapter surfaces for the specified query.  
  
## Polling message structure 
  
**Operation**: `Polling`

**XML Message**:  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Polling xmlns="http://schemas.microsoft.com/Sql/2008/05/Polling">
    <PolledData>
      <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">
        <any>[Value]</any>
        <any>[Value]</any>
        …
        </DataSet>
    </PolledData>
 </Polling>
```

**Description**: The inbound message that is sent by the SQL Server to the adapter clients.  


## TypedPolling message structure 

**Operation**: `TypedPolling`

**XML Message**:  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <TypedPollingResultSet xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedPolling">
    <COLUMN1>[Value]</Column1>
    <COLUMN2>[Value]</Column2>
    …
  </TypedPollingResultSet>
```

**Description**: The strongly-typed inbound message that is sent by the SQL Server to the adapter clients.
  
## Message Action for the Polling and TypedPolling Operations  
 The message action for the:  
  
-   Polling operation is “Polling.”  
  
-   TypedPolling operation is “TypedPolling.”  
  
