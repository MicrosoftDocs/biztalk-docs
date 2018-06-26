---
title: "Dynamic MLLP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e22fabb-0edf-4931-b8b2-74a5daccee4a
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Dynamic MLLP Adapter
Starting with [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)], the MLLP adapter properties can be configured at Runtime using a One-Way or Two-Way (Request-Response) send port.  
  
## Dynamic Properties  
 The following properties are in the **GlobalPropertySchemas** namespace:  
  
|Property|Description|  
|--------------|-----------------|  
|Message(MLLP.acceptableACKCodes)=”All ACK Codes”;|Values include:<br /><br /> -   All ACK Codes<br />-   AA and CA<br />-   AA, CA, AE and CE<br />-   AA, CA, AR and CR<br /><br /> This is similar to the **Acceptable ACK Codes** property in a Static MLLP Send Port.|  
|Message(MLLP.CarriageReturn)=”0d”;|ASCII Carriage Return Character|  
|Message(MLLP.endBlockDelimiter)=”1c”;|ASCII End Block Character|  
|Message(MLLP.startBlockDelimiter)=”0b”;|ASCII Start Block Character|  
|Message(MLLP.timeout)=”60000”;|Period after which inactive sending socket on BTAHL7 server will timeout(0 is no timeout)|  
|SendPortName(Microsoft.XLANGs.BaseTypes.Address) = “127.0.0.1:11000”;|Address and Port for routing the message|  
|SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) = “MLLP”;|Type of Adapter (MLLP)|  
  
## Additional  
  
- When creating a multipart message in an orchestration for HL7, create the message parts in this following order:  
  
  1. MSH Segment  
  
  2. BodySegments  
  
  3. ZSegments  
  
     If you specify the message parts in a different order, the following error occurs:  
  
     WrongBodyPartException  
  
- The adapter route properties can be specified on the orchestration to support dynamic routing.  
  
## See Also  
 [Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)   
 [MLLP Receive Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)