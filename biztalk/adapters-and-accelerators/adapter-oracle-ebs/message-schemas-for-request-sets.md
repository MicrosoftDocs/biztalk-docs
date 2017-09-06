---
title: "Message Schemas for Request Sets | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bba9677d-ee94-4da5-8611-b1e47f2f3798
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for Request Sets
Each request set in an Oracle application in Oracle E-Business Suite is surfaced as an operation in [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  
  
## Message Structure of Request Set Operation  
 The operations surfaced for request set follow a request-response message exchange pattern. The following table shows the structure of these request and response messages.  
  
> [!NOTE]
>  See entity descriptions after the table.  
  
|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|[Request_Set_Name] Request|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name] xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]/">   <SetRelClassOptions>     <Application>[value]</Application>     <ClassName>[value]</ClassName>     <CancelOrHold>[value]</CancelOrHold>     <StaleDate>[value]</StaleDate>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRelClassOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>   <SetNlsOptions>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetNlsOptions>   <StartTime><[value]</StartTime>   <[CONCURRENT_PROGRAM_NAME1]>[value]</[CONCURRENT_PROGRAM_NAME1]>   <[CONCURRENT_PROGRAM_NAME2]>[value]</[CONCURRENT_PROGRAM_NAME2]>   … </[Request_Set_Name]>`|- The [Request_Set_Name] operation takes five standard parameters:  `SetRelClassOptions`, `SetPrintOptions`,  `SetRepeatOptions`, `SetNlsOptions`, and `StartTime`.<br /><br /> - The `ContinueOnFail` parameter indicates whether the request set submission should continue or throw an exception in case the parent parameter (`SetRelClassOptions`, `SetPrintOptions`, `SetRepeatOptions` or `SetNlsOptions`) fails. You can specify **True** (continue) or **False** (throw an exception).<br /><br /> - For detailed information about each parameter, see [Operations on Request Sets](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md).|  
|[Request_Set_Name] Response|`<?xml version="1.0" encoding="utf-8" ?> <[Request_Set_Name]Response xmlns="[VERSION]/RequestSets/[APP_SHORT_NAME]">   <[Request_Set_Name]Result>[value]</[Request_Set_Name]Result> </[Request_Set_Name]Response>`|The response from Oracle E-Business Suite contains a concurrent request ID.|  
  
 Entity descriptions:  
  
 [VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05  
  
 .  
  
 [CONCURRENT_PROGRAM_NAME] = Concurrent program included in the request set.  
  
## Message Actions for Request Sets  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the following message actions for request sets.  
  
> [!NOTE]
>  See entity descriptions after the table.  
  
|Message|Action|Example|  
|-------------|------------|-------------|  
|Request Set request|RequestSets/[APP_SHORT_NAME]/[REQUESTSET_SHORT_NAME]|RequestSets/SQLGL/FNDRSSUB965|  
|Request Set response|RequestSets/[APP_SHORT_NAME]/[REQUESTSET_SHORT_NAME]]/response|RequestSets/SQLGL/FNDRSSUB965/response|  
  
 Entity descriptions:  
  
 [APP_SHORT_NAME] = Application short name.  
  
 [REQUESTSET_SHORT_NAME] = Request Set short name.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)