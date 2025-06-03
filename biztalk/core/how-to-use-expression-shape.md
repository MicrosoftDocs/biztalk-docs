---
description: "Learn more about: How to Use Expression Shape"
title: "How to Use Expression Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Use Expression Shape
The **Expression** shape enables you to enter any XLANG/s expression you choose in your orchestration. For example, you can make a .NET call to run an external program, or simply manipulate the values of your orchestration variables.  
  
 While the **Expression** shape is quite flexible, it is not good practice to use it to perform high-level orchestration logic, which preferably would be visible in the orchestration drawing itself. In general, it is easier to understand and maintain your orchestrations if your **Expression** shapes contain simple and modular expressions.  
  
### To configure an Expression shape  
  
1.  If BizTalk Expression Editor is not visible, right-click the **Expression** shape and click **Edit Expression** or, in the Properties window, click the Ellipsis (**...**) button for the **Expression** property.  
  
2.  In BizTalk Expression Editor, create an expression to assign values. For more information, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).  
  
## See Also  
 [XLANG-s Language](../core/xlang-s-language.md)
