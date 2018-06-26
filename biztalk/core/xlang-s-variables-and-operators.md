---
title: "XLANG-s Variables and Operators | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02512789-2cb9-4ba9-aa78-e59b248e6b24
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XLANG-s Variables and Operators
This section discusses the variables and operators used in the XLANG/s language.  
  
## XLANG/s Variables  
 Variables represent storage locations. Every variable has a type that determines what values can be stored in that variable. XLANG/s is type-safe, and its compiler guarantees that values stored in variables are always of the appropriate type. XLANG/s supports the following variable types:  
  
- Messages  
  
- Correlation sets  
  
- Service links  
  
- Ports  
  
- Distinguished built-in value types: **Boolean**, **Byte**, **Char**, **Decimal**, **Double**, **Int16**, **Int32**, **Int64**, **SByte**, **Single**, **String**, **UInt16**, **UInt32**, and **UInt64**  
  
- Objects  
  
- Enumeration types  
  
  XLANG/s provides initialization semantics for each of the preceding types. Such initialization can be viewed as an assignment to a variable of that type. In XLANG/s, a variable must be definitely assigned before its value can be obtained or used.  
  
## XLANG/s Operators  
 XLANG/s supports the following operators. They adhere closely to the functionality of the corresponding operators in C#.  
  
|Operator|Description|Example|  
|--------------|-----------------|-------------|  
|checked|Raises error on arithmetic overflow|checked(x = y * 1000)|  
|unchecked|Ignores arithmetic overflow|unchecked(x = y * 1000)|  
|new|Creates an instance of a class|myObject = new MyClass;|  
|typeof|Retrieves a type|myMapType = typeof(myMap)|  
|succeeded|Tests for successful completion of transactional scope or orchestration|succeeded(\<transaction ID for child transaction of current scope or service\>)|  
|exists|Tests for the existence of a message context property|BTS.RetryCount exists Message_In|  
|+|Unary plus|+(int x)|  
|-|Unary minus|-(int x)|  
|!|Logical negation|!myBool|  
|~|Bitwise complement|x = ~y|  
|()|Cast|(bool) myInt|  
|*|Times|Weight = MyMsg.numOrders * 20|  
|/|Divided by|x / y|  
|+|Plus|x + y|  
|-|Minus|x - y|  
|<<|Shift left|x << 2|  
|>>|Shift right|x >> 2|  
|<|Less than|If (MyMsg.numOrders < 10)...|  
|>|Greater than|If (MyMsg.numOrders > 10)...|  
|<=|Less than or equal to|If (MyMsg.numOrders <= 10)...|  
|>=|Greater than or equal to|If (MyMsg.numOrders >= 10)...|  
|==|Equal to|If (MyMsg.numOrders == 10)...|  
|!=|Not equal to|If (MyMsg.numOrders != 10)...|  
  
## See Also  
 [XLANG-s Data Types](../core/xlang-s-data-types.md)   
 [XLANG-s Statements](../core/xlang-s-statements.md)   
 [XLANG-s Expressions](../core/xlang-s-expressions.md)   
 [XLANG-s Reserved Words](../core/xlang-s-reserved-words.md)   
 [XLANG-s to BPEL4WS Type Conversions](../core/xlang-s-to-bpel4ws-type-conversions.md)