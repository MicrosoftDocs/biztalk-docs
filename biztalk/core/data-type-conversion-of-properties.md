---
title: "Data Type Conversion of Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MQSeries adapters, data type conversion"
  - "MQBYTE property [MQSeries adapters]"
  - "MQLONG property [MQSeries adapters]"
  - "MQCHAR property [MQSeries adapters]"
  - "configuring [MQSeries adapters], data type conversion"
ms.assetid: 5b81eab0-f7a1-42f3-b212-a211b2893fd5
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Data Type Conversion of Properties
Header properties in an MQSeries message are data structures contained in the message itself. The MQSeries adapter automatically validates and converts certain values in MQSeries message headers when sending and receiving messages.  
  
 The following table describes the MQSeries data types and their validation and conversion.  
  
|MQSeries data type|Validation and conversion|  
|------------------------|-------------------------------|  
|MQLONG|MQSeries performs the validation. Converts to a long integer. Values that are not valid prevent the message from going to the MQSeries queue.|  
|MQCHAR|Converts to a string.|  
|MQBYTE|Converts to a string that contains the characters 0-9 and a-f or A-F, representing the hexadecimal value of the number.|  
  
 Many of the MQSeries properties are 32-bit (4-byte) unsigned integers. Because **uint** is not a Common Language Specification (CLS)-compliant type, you must assign them to **object** types before using them in .NET methods.  
  
## See Also  
 [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md)   
 [Properties Related to BizTalk Server](../core/properties-related-to-biztalk-server.md)   
 [MQSeries Context Properties](../core/mqseries-context-properties.md)