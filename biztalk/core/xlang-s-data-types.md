---
title: "XLANG-s Data Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, expressions"
  - "Orchestration Designer, managing data"
  - "Orchestration Designer, variables"
  - "orchestrations, variables"
  - "Orchestration Designer, expressions"
ms.assetid: 5b08aaa6-1533-4bac-a76d-f9162e39bf4f
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XLANG-s Data Types
XLANG/s defines standard value types that are reflections of their C# counterparts. These include **Boolean**, **Byte**, **Char**, **Decimal**, **Double**, **Int16**, **Int32**, **Int64**, **SByte**, **Single**, **String**, **UInt16**, **UInt32**, and **UInt64**. XLANG/s supports single-dimensional arrays, but does not support array literals.  
  
 XLANG/s also has rich support for message handling. Messages can be based on schemas, .NET classes, Web message types (WSDL), or complex message types. XLANG/s supports the following complex data types:  
  
-   **messagetype.** This data type defines multipart message types which are defined as combinations of data elements and XSD-based messages and Method-Message types (messages that match the signature format of a method of a class or interface).  
  
-   **porttype.** This data type defines a collection of port operations that a port instance of that type can act upon.  
  
-   **correlationsettype.** This data type defines the data that will be used in any instance of a correlation set variable. Correlation set data is the routing mechanism used to ensure that messages moving through the system are dispatched to the appropriate running instance of a business process. For example, if a purchase order is sent to a trading partner for processing, it is imperative that the correct instance of the business process corresponding to that purchase order be invoked on its return.  
  
-   **servicelinktype.** This data type defines the set of **porttype** values that form a logically consistent group of ports used in a business process. The use of service links is a powerful mechanism that allows dynamic assignment to a group of ports at run time. This allows you to define a single business process that can be used to interact with multiple trading partners.  
  
## See Also  
 [XLANG-s Statements](../core/xlang-s-statements.md)   
 [XLANG-s Variables and Operators](../core/xlang-s-variables-and-operators.md)   
 [XLANG-s Expressions](../core/xlang-s-expressions.md)   
 [XLANG-s Reserved Words](../core/xlang-s-reserved-words.md)   
 [XLANG-s to BPEL4WS Type Conversions](../core/xlang-s-to-bpel4ws-type-conversions.md)