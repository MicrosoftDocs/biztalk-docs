---
title: "Constructing Web Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web messages, about Web messages"
  - "Web messages, message types"
  - "Web services, Web messages"
  - "Web messages, parts"
  - "Web messages"
  - "messages, Web messages"
ms.assetid: ca1792be-5fba-4f5d-a88e-b854f6a8ce33
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Constructing Web Messages
You construct a Web message from a Web message type. When you add a Web reference, BizTalk automatically creates Web message types, which BizTalk creates based on the Web methods from the added Web service. You add a Web message to your orchestration, setting the message type to one of the Web message types. You create individual message parts based on primitive .NET or schema types. You can construct a Web message that contains no message parts.  
  
 **Web message types**  
  
 Web message types, defined in the Reference.odx, are identical to a normal message type, except you cannot modify, rename or delete them. To delete a Web message type, you must remove the Web reference from your BizTalk project.  
  
 BizTalk project creates one request and one response Web message type for each Web method in the added Web service. If the Web method is a one-way operation, BizTalk only creates a request Web message type. A request Web message type contains one message part for each input parameter of the Web method. A response Web message type contains one message part for the return value and one message part for each output parameter of the Web method.  
  
 Depending on the Web method parameter (input or output), BizTalk creates a Web message type from a primitive .NET type or a schema type. If the Web method parameter is a primitive .NET type, the message part uses a primitive .NET type. If the Web method parameter is a schema type, BizTalk adds the schema type to the BizTalk project as a schema in Reference.xsd. The schema is the basis for the message part. You can find Reference.xsd in the Web references folder.  
  
 Alternatively, you can create both primitive and schema .NET types by calling a .NET class. For more information on creating message types by using a .NET class, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).  
  
 **Web messages**  
  
 Web messages are the messages you use when you consume (call) a Web service. You add a Web message to an orchestration the same way that you add a regular message, except that you set the message type to one of the Web message types that BizTalk created when you added a Web reference.  
  
 **Message parts**  
  
 After you create the Web message, you construct the individual message parts. If your message part uses a primitive .NET type, you use a **Message Assignment** shape. If your message part uses a schema type, you use a **Transform** shape or **Message Assignment** shape. For more information, see [Constructing Messages in User Code](../core/constructing-messages-in-user-code.md).  
  
## In This Section  
  
-   [How to Add Web Messages](../core/how-to-add-web-messages.md)  
  
-   [How to Determine a Web Message Part Type](../core/how-to-determine-a-web-message-part-type.md)  
  
-   [How to Construct a Web Message Part from a Primitive .NET Type](../core/how-to-construct-a-web-message-part-from-a-primitive-net-type.md)  
  
-   [How to Construct a Web Message Part from a Schema Type](../core/how-to-construct-a-web-message-part-from-a-schema-type.md)  
  
-   [How to Construct a Web Message with No Message Parts](../core/how-to-construct-a-web-message-with-no-message-parts.md)