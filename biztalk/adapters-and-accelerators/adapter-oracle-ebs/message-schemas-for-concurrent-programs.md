---
description: "Learn more about: Message Schemas for Concurrent Programs"
title: "Message Schemas for Concurrent Programs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c5709d5-e2b3-485b-9cdd-004985972ba1
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for Concurrent Programs
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces concurrent programs as operations. Along with the concurrent programs exposed as operations, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] also surfaces the following three standard operations: Get_Status, Wait_For_Request, and Submit_Request. For information about these operations related to concurrent programs, see [Operations on Concurrent Programs](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).  
  
## Message Structure of Concurrent Program Operations  
 The operations surfaced for concurrent programs follow a request-response message exchange pattern. The following table shows the structure of these request and response messages.  
  
> [!NOTE]
>  See entity descriptions after the table.  
  
|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|[Concurrent_Program_Name] Request|`<?xml version="1.0" encoding="utf-8" ?> <[Concurrent_Program_Name] xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]/">   <SetOptions>     <Implicit>[value]</Implicit>     <Protected>[value]</Protected>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>   <Description>[value]</Description>   <StartTime><[value]</StartTime>   <[CONCURRENT_PROGRAM_ARGUMENT1]>[value]</[CONCURRENT_PROGRAM_ARGUMENT1]>   <[CONCURRENT_PROGRAM_ARGUMENT2]>[value]</[CONCURRENT_PROGRAM_ARGUMENT2]>   … </[Concurrent_Program_Name]>`|- The [Concurrent_Program_Name] operation takes five standard parameters: *SetOptions*, *SetPrintOptions*, *SetRepeatOptions*, *Description*, and *StartTime*.<br /><br /> - The *ContinueOnFail* parameter indicates whether the concurrent request submission should continue in case the parent parameter (*SetOptions*, *SetPrintOptions*, or *SetRepeatOptions*)     fails, or whether it should throw an exception. You can specify **True** (continue) or **False** (throw an exception).<br /><br /> - For detailed information about each parameter, see [Operations on Concurrent Programs](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|[Concurrent_Program_Name] Response|`<?xml version="1.0" encoding="utf-8" ?> <[Concurrent_Program_Name]Response xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <[Concurrent_Program_Name]Result>[value]</[Concurrent_Program_Name]Result> </[Concurrent_Program_Name]Response>`|The response from Oracle E-Business Suite contains a concurrent request ID.|  
|Get_Status Request|`<?xml version="1.0" encoding="utf-8" ?> <GetStatusForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <RequestId>[value]</RequestId>  </GetStatusForConcurrentProgram>`|This Get_Status request message takes the request ID of a concurrent program as an input.|  
|Get_Status Response|`<?xml version="1.0" encoding="utf-8" ?> <GetStatusForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <GetStatusForConcurrentProgramResult>[value]</GetStatusForConcurrentProgramResult>    <Phase>[value]</Phase>    <Status>[value]</Status>    <DevPhase>[value]</DevPhase>    <DevStatus>[value]</DevStatus>    <Message>[value]</Message>  </GetStatusForConcurrentProgramResponse>`|This Get_Status response message returns the request phase/status and the completion message of a concurrent program.<br /><br /> For detailed information about each parameter, see [Operations on Concurrent Programs](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|Wait_For_Request Request|`<?xml version="1.0" encoding="utf-8" ?> <WaitForRequestForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <RequestId>[value]</RequestId>   <Interval>[value]</Interval>   <MaxWait>[value]</MaxWait>    </WaitForRequestForConcurrentProgram>`|For detailed information about each parameter, see [Operations on Concurrent Programs](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|Wait_For_Request Response|`<?xml version="1.0" encoding="utf-8" ?> <WaitForRequestForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <WaitForRequestForConcurrentProgramResult>[value]</WaitForRequestForConcurrentProgramResult>    <Phase>[value]</Phase>    <Status>[value]</Status>    <DevPhase>[value]</DevPhase>    <DevStatus>[value]</DevStatus>    <Message>[value]</Message>    </WaitForRequestForConcurrentProgramResponse>`|This Wait_For_Request response message returns the request phase/status and the completion message of a concurrent program.<br /><br /> For detailed information about each parameter, see [Operations on Concurrent Programs](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|Submit_Request Request|`<?xml version="1.0" encoding="utf-8" ?> <SubmitRequestForConcurrentProgram xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <SetOptions>     <Implicit>[value]</Implicit>     <Protected>[value]</Protected>     <Language>[value]</Language>     <Territory>[value]</Territory>     <ContinueOnFail>[value]</ContinueOnFail>   </SetOptions>   <SetPrintOptions>     <Printer>[value]</Printer>     <Style>[value]</Style>     <Copies>[value]</Copies>     <SaveOutput>[value]</SaveOutput>     <PrintTogether>[value]</PrintTogether>     <ContinueOnFail>[value]</ContinueOnFail>   </SetPrintOptions>   <SetRepeatOptions>     <RepeatTime>[value]</RepeatTime>     <RepeatInterval>[value]</RepeatInterval>     <RepeatUnit>[value]</RepeatUnit>     <RepeatType>[value]</RepeatType>     <RepeatEndTime>[value]</RepeatEndTime>     <ContinueOnFail>[value]</ContinueOnFail>   </SetRepeatOptions>     <Program>[value]</Program>   <Description>[value]</Description>   <StartTime>[value]</StartTime>   <Arguments>[array_of_strings</Arguments>    </SubmitRequestForConcurrentProgram>`|For detailed information about each parameter, see [Operations on Concurrent Programs](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md).|  
|Submit_Request Response|`<?xml version="1.0" encoding="utf-8" ?> <SubmitRequestForConcurrentProgramResponse xmlns="[VERSION]/ConcurrentPrograms/[APP_SHORT_NAME]">   <SubmitRequestForConcurrentProgramResult>[value]</SubmitRequestForConcurrentProgramResult>  </SubmitRequestForConcurrentProgramResponse>`|If the submit request completes successfully, the response message returns the concurrent request ID. Otherwise, it returns “0”.|  
  
 Entity descriptions:  
  
 [VERSION] = http://schemas.microsoft.com/OracleEBS/2008/05  
  
 [APP_SHORT_NAME] = Application short name  
  
 [CONCURRENT_PROGRAM_ARGUMENT] = Argument expected by the concurrent program as defined in Oracle E-Business Suite  
  
## Message Actions for Concurrent Programs  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the following message actions for concurrent programs.  
  
> [!NOTE]
>  See entity descriptions after the table.  
  
|Message|Action|Example|  
|-------------|------------|-------------|  
|[Concurrent_Program_Name] Request|ConcurrentPrograms/[APP_SHORT_NAME]/[CONCURRENT_PROGRAM_SHORT_NAME]|ConcurrentPrograms/SQLGL/ADSFINS|  
|[Concurrent_Program_Name] Response|ConcurrentPrograms/[APP_SHORT_NAME]/[CONCURRENT_PROGRAM_SHORT_NAME]/response|ConcurrentPrograms/SQLGL/ADSFINS/response|  
|Get_Status Request|ConcurrentPrograms/[APP_SHORT_NAME]/GetStatusForConcurrentProgram|ConcurrentPrograms/SQLGL/GetStatusForConcurrentProgram|  
|Get_Status Response|ConcurrentPrograms/[APP_SHORT_NAME]/GetStatusForConcurrentProgram/response|ConcurrentPrograms/SQLGL/GetStatusForConcurrentProgram/response|  
|Wait_For_Request Request|ConcurrentPrograms/[APP_SHORT_NAME]/WaitForRequestForConcurrentProgram|ConcurrentPrograms/SQLGL/WaitForRequestForConcurrentProgram|  
|Wait_For_Request Response|ConcurrentPrograms/[APP_SHORT_NAME]/WaitForRequestForConcurrentProgram/response|ConcurrentPrograms/SQLGL/WaitForRequestForConcurrentProgram/response|  
|Submit_Request Request|ConcurrentPrograms/[APP_SHORT_NAME]/SubmitRequestForConcurrentProgram|ConcurrentPrograms/SQLGL/SubmitRequestForConcurrentProgram|  
|Submit_Request Response|ConcurrentPrograms/[APP_SHORT_NAME]/SubmitRequestForConcurrentProgram/response|ConcurrentPrograms/SQLGL/SubmitRequestForConcurrentProgram/response|  
  
 Entity descriptions:  
  
 [APP_SHORT_NAME] = Application short name  
  
 [CONCURRENT_PROGRAM_SHORT_NAME] = Concurrent Program short name  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)
