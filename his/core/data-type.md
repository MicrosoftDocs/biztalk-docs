---
title: "Data Type2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1cb98516-1533-404a-86fe-a38ab8ae440f
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Data Type
Header properties in MQSeries messages are data structures contained in the message itself. The adapter automatically validates and converts certain values in MQSeries message headers when sending and receiving messages.  
  
 The following table describes the MQSeries data types and their validation and conversion.  
  
|MQSeries Data Type|Validation and Conversion|  
|------------------------|-------------------------------|  
|MQLONG|MQSeries performs the validation. Converts to a long integer. Values that are not valid prevent the message from going to the MQSeries queue.|  
|MQCHAR|Converts to a string.|  
|MQBYTE|Converts to a string that contains the characters 0-9, and a-f or A-F, representing the hexadecimal value of the number.|  
  
 Many of the MQSeries properties are 32-bit (4-byte) unsigned integers. Because uint is not a Common Language Specification (CLS)-compliant type, you must assign them to object types before using them in .NET methods. For more information about CLS-compliant types, see "What Is the Common Language Specification?" in .NET Framework Help.  
  
## See Also  
 [Client-Based BizTalk Adapter for WebSphere MQ Programmer's Reference](../core/client-based-biztalk-adapter-for-websphere-mq-programmer-s-reference.md)