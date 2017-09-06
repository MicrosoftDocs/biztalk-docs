---
title: "Using Operators in Expressions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, operators"
  - "XLANG/s, operators"
  - "orchestrations, XLANG/s"
ms.assetid: f0948ce2-c508-48aa-af79-d207f577b22f
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Operators in Expressions
The following XLANG/s operators are available for use in orchestration expressions. They adhere closely to the functionality of the corresponding operators in C#.  
  
|Operator|Description|Example|  
|--------------|-----------------|-------------|  
|checked()|raise error on arithmetic overflow|checked(x = y * 1000)|  
|unchecked()|ignore arithmetic overflow|unchecked(x = y * 1000)|  
|new|create an instance of a class|myObject = new MyClass;|  
|typeof|Type retrieval|myMapType = typeof(myMap)|  
|succeeded()|test for successful completion of transactional scope or orchestration|succeeded(\<transaction ID for child transaction of current scope or service>)|  
|exists|test for the existence of a message context property|BTS.RetryCount exists Message_In|  
|+|unary plus|+(int x)|  
|-|unary minus|-(int x)|  
|!|logical negation|!myBool|  
|~|bitwise complement|x = ~y|  
|()|cast|(bool) myInt|  
|*|times|Weight = MyMsg.numOrders * 20|  
|/|divided by|x / y|  
|+|plus|x + y|  
|-|minus|x - y|  
|<<|shift left|x <\< 2|  
|>>|shift right|x >> 2|  
|<|less than|If (MyMsg.numOrders \< 10)...|  
|>|greater than|If (MyMsg.numOrders > 10)...|  
|<=|less than or equal to|If (MyMsg.numOrders \<= 10)...|  
|>=|greater than or equal to|If (MyMsg.numOrders >= 10)...|  
|==|equal to|If (MyMsg.numOrders == 10)...|  
|!=|not equal to|If (MyMsg.numOrders != 10)...|  
|&|and|If (myByte & 255)...|  
|^|exclusive or|If (myByte ^ 1)...|  
|&#124;|or|If (myByte &#124; 1)...|  
|&&|conditional and|If (MyMsg.numOrders > 10) && (MyMsg.numOrders < 100)|  
|&#124;&#124;|conditional or|If (MyMsg.numOrders \< 10) &#124;&#124; (MyMsg.numOrders > 100)|  
|//|commenting|//This is the comment|  
  
> [!NOTE]
>  The rules differ between general expressions and filter expressions that are used with the **Receive** shape.  
  
## See Also  
 [Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md)