---
description: "Learn more about: Data Type"
title: "Data Type2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [Client-Based BizTalk Adapter for WebSphere MQ Programmer's Reference](../core/client-based-biztalk-adapter-for-websphere-mq-programmer-s-reference2.md)
