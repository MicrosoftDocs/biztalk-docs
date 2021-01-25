---
description: "Learn more about: Message Schemas for the Polling Operations"
title: "Message Schemas for the Polling Operations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "POLLINGSTMT operation, message actions for"
  - "POLLINGSTMT operation, message structure for"
ms.assetid: b82edcc2-9437-4c7b-ba2b-7b966fff3f15
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for the Polling Operations
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces various inbound operations related to polling depending on the target object on the Oracle database. To poll tables and views, a single POLLINGSTMT operation is surfaced whereas each stored procedure, functions, and packaged procedures and functions are exposed as inbound operations for polling.  
  
 You can specify a **PollingId** parameter in the query string of the connection URI to qualify the namespace of the POLLINGSTMT operation. Setting this parameter only qualifies the namespace of the POLLINGSTMT operation; it does not change the message action. For more information about the Oracle Database adapter connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
 You configure the polling operations by setting binding properties in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. For more information about these binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). You set the **PollingStatement** binding property to specify a SQL statement, stored procedure, function or a procedure within a package for the polling query. The result set of this query is returned as data to your code in the polling operation.  
  
## Message Structure for the Polling Operations  
 The following table shows the XML message structure for the various polling operations.  
  
|Operation|Target Object|XML Message|Description|  
|---------------|-------------------|-----------------|-----------------|  
|POLLINGSTMT|- Tables<br /><br /> - Views|`<?xml version="1.0" encoding="utf-8" ?>  <POLLINGSTMT xmlns="[VERSION]/POLLINGSTMT[POLLING_ID]">   <POLLINGSTMTRECORD>     <POLLINGSTMTRECORD>       <FIELD1_NAME>val1</FIELD1_NAME>        <FIELD2_NAME>val2</FIELD2_NAME>       …     </POLLINGSTMTRECORD>      …    </POLLINGSTMTRECORD> </POLLINGSTMT>`|The structure of the result set contained in the POLLINGSTMTRECORD types is determined by the metadata that the adapter surfaces for the SQL SELECT query.<br /><br /> The namespace of the POLLINGSTMT operation is determined by the PollingId parameter in the connection URI.|  
|[CustomPollingOperation]|- Stored Procedures<br /><br /> - Functions<br /><br /> - Packages|**Stored Procedures**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/[SCHEMA]/PollingProcedure">    <[CustomPollingOperation]Result>      <PRM1>[Value]</PRM1>      <PRM2>[Value]</PRM2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **Functions**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?> <[CustomPollingOperation] xmlns="[Version]/[Schema]/PollingFunction">    <[CustomPollingOperation]Result>      <COL1>[Value]</COL1]>      <COL2>[Value]</COL2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **Packages**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/[Schema]/PollingPackage/[PACKAGE_NAME]/">    <[CustomPollingOperation]Result>[Value]</[CustomPollingOperation]Result> </[CustomPollingOperation]>`|The structure of the result set in the polling operation is determined by the data type of the elements in the target object.|  
  
 [Version] = http://Microsoft.LobServices.OracleDB/2007/03.  
  
 [CustomPollingOperation] = It is the same as the stored procedure, function, or packaged procedure or function name that are exposed as the inbound polling operation.  
  
 [Schema] = Name of the Oracle schema. For example, SCOTT.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)
