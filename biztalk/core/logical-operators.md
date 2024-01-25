---
description: "Learn more about: Logical Operators"
title: "Logical Operators"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Logical Operators
The Business Rules Framework supports using the logical AND, logical OR, and logical NOT operators in creating business rules. The following table describes the logical operators.  
  
|Logical Operator|Description|  
|----------------------|-----------------|  
|**AND**|Returns **true** if both the operands evaluate to **true**; otherwise returns **false**.|  
|**OR**|Returns **true** if one of the operands evaluates to **true**, otherwise returns **false**.|  
|**NOT**|Returns **true** if the operand evaluates to **false**, otherwise returns **false**.|  
  
 When operands are of different types, the rule engine converts type of one of the parameters to match the type of the other parameter or converts types of both the parameters to a common type before evaluating the expression.  
  
## To use a logical operator in a business rule  
 Use the following procedure to use a logical operator in a business rule.  
  
1.  In the **IF** pane of Business Rule Composer, right-click the **Conditions** node, and then select the logical operator that you wish to add to the logical expression.  
  
2.  Right-click the logical operator, and add the predicates or nested logical operators you want to add.  
  
## See Also  
 [Arithmetic Operators](../core/arithmetic-operators.md)
