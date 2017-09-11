---
title: "How to Use Expressions to Create Objects and Call Object Methods | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, parameters"
  - "Expression shape [Orchestration Designer], calling objects"
  - "Expression shape [Orchestration Designer], parameters"
  - "Expression shape [Orchestration Designer], passing messages"
  - "orchestrations, methods"
  - "Expression shape [Orchestration Designer], calling methods"
  - "orchestrations, objects"
  - "Expression shape [Orchestration Designer], warning"
  - "Use Default Constructor property"
  - ".NET member invocation"
ms.assetid: b6af67eb-8ba5-4c95-9b63-26ebb6617af0
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use Expressions to Create Objects and Call Object Methods
You might need to use expressions to create objects or invoke methods.  
  
## Creating objects  
 To create a variable that has a type which is a .NET class, you construct an object in the **Expression** shape. The properties of your .NET class variable include a constructor. If you use the default constructor, you simply declare the variable directly as you would any other variable, like one of type bool or int.  
  
 If you use a constructor that takes parameters, you use the keyword **new**, followed by the object class and any parameters in parentheses:  
  
```  
new MyClass(myParam1, myParam2)  
```  
  
> [!CAUTION]
>  The **Use Default Constructor** property might not be displayed for some objects that do, in fact, have constructors. In this case, the default constructor will be used automatically, and an error will be raised if you attempt to use a different constructor.  
  
## Invoking methods  
 To invoke a method on a .NET class object, you append a period and the name of the method to the object reference, followed by any parameters in parentheses:  
  
```  
MyObject.MyMethod (param1)  
```  
  
## Passing and using messages as parameters  
 To pass a message as a parameter to a method call on a .NET class, you first add a reference to Microsoft.XLANGs.BaseTypes.dll in the project that defines the class, and then use the type XLANGMessage in the method signature.  
  
 Referencing the multi-part message type enables you to access the various parts of the message by using the type XLANGPart:  
  
```  
MyMethod(XLANGMessage myMsg)  
{  
XLANGPart myPart = myMsg["Part1"];  
XmlDocument xmlDoc = (XmlDocument) myPart.RetrieveAs(typeof(XmlDocument));  
}  
```  
  
 In the call itself, you simply supply the name of the message as you would any other parameter:  
  
```  
MyObject.MyMethod(myMessage)  
```  
  
 You can also pass a message part as type XLANGPart.  
  
## .NET member invocation  
 You can access public members except in the case of direct access to members of a message part. To directly access a member of a message part it must be promoted as a distinguished field.  
  
## COM/COM+ component invocation  
 XLANGs generates C# code. All user-declared XLANGs variables are generated as C# variables. There is no special behavior except in the case of atomic transactions. When a serviced component (that is, an instance of a class that implements **System.EnterpriseServices.ServicedComponent**) is declared in an atomic scope, then and only then does XLANGs generate and use a real DTC COM+ transaction.  
  
 If a variable is referenced as an L-value (that is, it is written to) in the atomic scope, but is declared in an outer scope, the variable is cloned to support rollback. However, an object (such as an **XmlDocument**) can be modified inside a .NET function call when passed as an in-parameter, and thus XLANGs will miss that the object is being written to and it will not roll back correctly. The workaround in this case is to pass such objects as ref parameters.  
  
 The bottom line is that components should behave as they do in other C# programs.  
  
## See Also  
 [About BizTalk Message Context Properties](../core/about-biztalk-message-context-properties.md)