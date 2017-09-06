---
title: "XLANG-s Language | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, properties"
ms.assetid: 97b62f17-5a8d-4d87-8563-1f6d941f027f
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# XLANG-s Language
XLANG/s was designed to use Internet standards such as XML, XSD, and Web Services Description Language (WSDL), and has embedded support for working with .NET-based objects and messages. XLANG/s can be viewed as a messaging language with some of the expression capabilities of C#. However, code is not portable between XLANG/s and C#.  
  
 XLANG/s encourages a clear separation between process and implementation. For example, the business process or protocol is specified in XLANG/s, and the local aspects of the application, such as database access, are implemented in other .NET programming languages such as C# or Visual Basic.NET.  
  
 XLANG/s assignment and expression syntax is modeled after C#, and you should reference the C# specification for exact syntax. XLANG/s defines a rich set of high-level constructs that are used to define business processes. While XLANG/s provides support for low-level data types like string and integer, high-level data types are also defined: messages, ports, correlations, and service links. These data types are used to rigorously define the semantics associated with a business process, and are complemented by process control statements such as **while** or **scope**.  
  
 XLANG/s statements generally fall into one of two categories: simple statements that act on their own, such as **receive** or **send**, and complex statements that contain or group either simple statements or other complex statements, such as **scope**, **parallel**, and **listen**. The semantics embodied in XLANG/s are a reflection of those defined in the Business Process Execution Language for Web Services (BPEL4WS) specification published by Microsoft, IBM, and BEA for the definition of business process semantics.  
  
 Understanding the main constructs of XLANG/s is optional because they are produced as a result of drawing orchestration diagrams in BizTalk Orchestration Designer. Orchestration Designer is a rich graphical tool for visually designing business processes. It generates XLANG/s files that have an .odx extension and contain additional visual information in their headers and custom attribute information in their bodies.  
  
> [!NOTE]
>  The XLANG/s language is proprietary and is not fully documented. This section exposes certain parts of the language that you might need to be aware of as you develop your orchestrations. Direct modification of the .odx files is not supported.  
  
## XLANG/s Programs  
 The simplest XLANG/s program requires that a message type be defined, which gives the orchestration some data to start to work with. The orchestration receives the message over a port and then terminates. The following code is an example:  
  
```  
module HelloWorldApp  
{  
     private porttype ptPOReceive  
     {  
      oneway opPOReceive  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private porttype ptPOSend  
     {  
      oneway opPOSend  
      {  
       HelloWorldApp.PurchaseOrder  
      }  
     }  
     private service  HelloWorld  
     {  
      port implements HelloWorldApp.ptPOReceive poPOReceive;  
      port uses HelloWorldApp.ptPOSend poPOSend;  
      message HelloWorldApp.PurchaseOrder msgPO;  
      body ()  
      {  
       activate receive (poPOReceive.opPOReceive, msgPO);  
       send (poPOSend.opPOSend, msgPO);  
       }  
     }  
}  
```  
  
 In the preceding XLANG/s program, the `module` keyword defines the unit of compilations for an XLANG/s program. All types used in the program—such as **porttype**, **correlationsettype**, **servicelinktype**, and **messagetype**—are scoped at this level.  
  
 A port is a construct that XLANG/s can send or receive messages to or from, and the port has a defined type called **porttype**. The **porttype** construct defines a collection of operations that can be used on the port. These operations define a single valid message exchange over the port. In defining **porttype**, **messagetype**, **servicelinktype**, or **correlationsettype** constructs, the author of an XLANG/s program is essentially creating complex data type definitions. These definitions have the same advantages as complex data types do in other languages: They abstract the notions embodied in the data type to a higher level, and they allow for easy reuse of the data type.  
  
 The **ptPOReceive** port in the preceding HelloWorldApp module is defined with a one-way receive port operation, **opPOReceive**. The service HelloWorld block defines the actual implementation of the process and any variables it may use, including port and message variables. The first three lines of code within this block define the port variables **poPOReceive** and **poPOSend** and the message **msgPO** respectively. The body contains the code describing parameters to the service and the execution behavior. All variables, unless defined with a nested scope block, are scoped to this level. The receive statement, which is an activate receive, receives the **msgPO** message from the **poPOReceive.opPOReceive** port and creates a new instance of the orchestration. After the message is received, the send statement directs the message to a send port. In the two port declarations in the preceding code, **poPOReceive** uses the implements modifier, whereas **poPOSend** uses the uses modifier. The implements modifier tells the runtime it will be receiving a message over that port. The uses modifier tells the runtime that it will be sending a message over that port.  
  
## In This Section  
  
-   [XLANG-s Data Types](../core/xlang-s-data-types.md)  
  
-   [XLANG-s Statements](../core/xlang-s-statements.md)  
  
-   [XLANG-s Variables and Operators](../core/xlang-s-variables-and-operators.md)  
  
-   [XLANG-s Expressions](../core/xlang-s-expressions.md)  
  
-   [XLANG-s Reserved Words](../core/xlang-s-reserved-words.md)  
  
-   [XLANG-s to BPEL4WS Type Conversions](../core/xlang-s-to-bpel4ws-type-conversions.md)  
  
## See Also  
 [About the BizTalk Orchestration Engine](../core/about-the-biztalk-orchestration-engine.md)