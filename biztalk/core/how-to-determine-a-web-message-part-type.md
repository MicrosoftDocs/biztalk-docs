---
description: "Learn more about: How to Determine a Web Message Part Type"
title: "How to Determine a Web Message Part Type | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web messages, message types"
  - "Web services, Web messages"
  - "Web messages, parts"
ms.assetid: bdd1f604-ec35-41e3-b5a8-1e0ad0193eff
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Determine a Web Message Part Type
You can determine if a Web message part type is a primitive .NET type or a schema type by using the Properties window for a given Web message type.  
  
### To determine a Web message part type  
  
1.  With an orchestration open, on the **View** menu, click **Other Windows**,and then click **Orchestration View**.  
  
2.  Expand the **Multi-part Message Types** node, and then expand a Web message type.  
  
3.  Select a message part.  
  
     A Web message part signature that begins as **\<*project default namespace*\>.\<*Web reference name*\>.Reference.\<*schema root*\>** is a schema type. The **\<*schema root*\>** part of the type is the root element of the Web reference schema that constructs the Web message part. Otherwise, the message part signature is a primitive .NET type such as **System.String** or **System.Int32**.  
  
## See Also  
 [Constructing Web Messages](../core/constructing-web-messages.md)
