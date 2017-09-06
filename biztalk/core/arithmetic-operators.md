---
title: "Arithmetic Operators | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d73e153c-aac1-4cea-92d8-af4a1bea6e6a
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Arithmetic Operators
The Business Rules Framework supports using the addition, subtraction, multiplication, division, and remainder (modulo) operators in creating business rules. The following table describes the arithmetic operators.  
  
|Arithmetic operator|Description|  
|-------------------------|-----------------|  
|**Add**|Represents the addition operator (arg1 added to arg2).|  
|**Subtract**|Represents the subtraction operator (arg1 subtracted from arg2).|  
|**Multiply**|Represents the multiplication operator (arg1 multiplied by arg2).|  
|**Divide**|Represents the division operator (arg1 divided by arg2).|  
|**Remainder**|Represents the remainder operator (arg1 modulo arg2).|  
  
 When operands are of different types, automatic numeric promotion occurs with the smaller operand type being converted to the larger operand type. For example, if the **Add** operator is used with the first operand of **int** type and the second operand of **long** type, the type of the first operand is converted to **long** before performing the **Add** operation. The rule engine also supports double promotion if both the operands can be promoted to a common type. For example, if the **Add** operator is used with the first operand of **int** type and the second operand of **uint** type, the types of both operands are converted to **long** before performing the **Add** operation.  
  
## To use a logical operator in a business rule  
 Use the following procedure to use a logical operator in a business rule.  
  
1.  In the Facts Explorer window, click the **Vocabularies** tab.  
  
2.  Expand **Vocabularies**, expand **Functions**, expand **Version 1.0 - Published**, and then drag the **Add/Subtract/Multiply/Divide/Remainder** to the Conditions pane/Actions pane.  
  
3.  Specify values for left and right operators.  
  
## See Also  
 [Logical Operators](../core/logical-operators.md)