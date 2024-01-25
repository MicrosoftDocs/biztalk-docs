---
description: "Learn more about: Shapes that Take Expressions"
title: "Shapes that Take Expressions"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Shapes that Take Expressions
Several shapes in Orchestration Designer, including **Decide** and **Loop**, use Boolean expressions to form rules that control branching. Other shapes use expressions for other purposes. You can create or edit an expression for these shapes by using BizTalk Expression Editor.  
  
 The following table summarizes the shapes that use expressions in Orchestration Designer and lists the data types that are valid for those expressions.  
  
|Shape|Description of expression use|Valid expression data types|  
|-----------|-----------------------------------|---------------------------------|  
|**Decide**|**Decide** shapes contain **Rule** shapes, which use Boolean expressions.|Boolean|  
|**Receive**|**Receive** shapes that have the Activate property set to True use the **Filter Expression** property to filter incoming messages. The expression in this property must evaluate to a Boolean, whose value determines whether or not to accept an incoming message.<br /><br /> The **Filter Expression** dialog box is used to create filter expressions.|Boolean|  
|**Loop**|A **Loop** shape requires a **Rule** shape, which in turn must contain a Boolean expression.|Boolean|  
|**Rule**|**Rule** shapes (displayed on the Process Area as "branch" shapes) are simple shapes that contain Boolean expressions and are used within other (complex) shapes to govern branching.|Boolean|  
|**Listen**|Each branch of a **Listen** shape contains, at a minimum, either a **Receive** shape, which uses a Boolean expression only for filter expressions (see the entry for **Receive**), or a **Delay** shape, which uses a **System.DateTime** object or **System.TimeSpan** object.|Boolean, System.DateTime, System.TimeSpan|  
|**Delay**|The expression used in a **Delay** shape must evaluate to a **System.DateTime** object, to express a deadline, or a **System.TimeSpan** object, to express duration.|System.DateTime, System.TimeSpan|  
|**Message Assignment**|The expression in a **Message Assignment** shape assigns a value to a message. The value assigned can be of any type, though typically a message is assigned.|Any|  
|**Expression**|The **Expression** shape enables you to enter any expression you choose in your orchestration. For example, you can make a .NET call to run an external program, or simply manipulate the values of your orchestration variables.|Any|  
  
## In This Section  
 [How to Use Expression Shape](../core/how-to-use-expression-shape.md)  
  
## See Also  
 [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md)   
 [Constructing Messages](../core/constructing-messages.md)   
 [Configuring Flow Control Shapes](../core/configuring-flow-control-shapes.md)
