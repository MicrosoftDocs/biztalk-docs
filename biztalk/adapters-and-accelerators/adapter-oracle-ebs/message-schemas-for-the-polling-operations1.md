---
description: "Learn about the message schemas for polling operations used by the Microsoft BizTalk Adapter for Oracle E-Business Suite."
title: "Message Schemas for the Polling Operations1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c572c4ec-0a3f-42b8-bebd-40eb584438ad
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for the Polling Operations

The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces various inbound operations related to polling depending on the target object in Oracle E-Business Suite. For interface tables, interface views, tables, and views, a single Poll operation is surfaced whereas you can have multiple custom polling operations for PL/SQL APIs, functions, and stored procedures.  
  
 You configure the polling operations by setting binding properties in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. For more information about these binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). You set the **PollingStatement** binding property to specify a SQL statement, stored procedure, function or a procedure within a package for the polling query. The result set of this query is returned as data to your code in the polling operation.  
  
## Message Structure for the Polling Operations
  
The following table shows the XML message structure for the various polling operations.  
  
> [!NOTE]
> See entity descriptions after the table.  
  
|Operation|Target Object|XML Message|Description|  
|---------------|-------------------|-----------------|-----------------|  
|Poll|- Interface Tables<br /><br /> - Interface Views<br /><br /> - Tables<br /><br /> - Views|`<?xml version="1.0" encoding="utf-8" ?>  <Poll xmlns="[Version]/[TargetObject]/[Schema]/[TargetObject_Name]">    <DATA>      <SelectRecord>        <Column1>[Value]</Column1>        <Column2>[Value]</Column2>        …        </SelectRecord>    </DATA> </Poll>`|For example, the XML message for the Poll operation on Interface Tables will be as follows:<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <Poll xmlns="[Version]/InterfaceTables/[Schema]/[InterfaceTable_Name]">    <DATA>      <SelectRecord>        <Column1>[Value]</Column1>        <Column2>[Value]</Column2>        …        </SelectRecord>    </DATA> </Poll>`|  
|[CustomPollingOperation]|- PL/SQL APIs<br /><br /> - Stored Procedures<br /><br /> - Functions|**PL/SQL APIs**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/PollingPackageAPis/[Schema]/[PL/SQL API]">    <[CustomPollingOperation]Result>[Value]</[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **Functions**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?> <[CustomPollingOperation] xmlns="[Version]/PollingFunctions/[Schema]">    <[CustomPollingOperation]Result>      <COL1>[Value]</COL1]>      <COL2>[Value]</COL2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **Stored Procedures**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/PollingFunctions/[Schema]">    <[CustomPollingOperation]Result>      <PRM1>[Value]</PRM1>      <PRM2>[Value]</PRM2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`|The structure of the result set in the polling operation is determined by the data type of the elements in the target object.|  
  
 Entity descriptions:  
  
 [Version] = `http://schemas.microsoft.com/OracleEBS/2008/05`.  
  
 [CustomPollingOperation] = Name of the custom polling operation.  
  
 [Schema] = Name of the Oracle schema. For example, SCOTT.  
  
 [PL/SQL API] = Name of the PL/SQL API on which a custom polling operation is performed.  
  
## See Also
  
[Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)
