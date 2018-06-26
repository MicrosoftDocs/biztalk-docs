---
title: "Ways to Use Message Content to Control Message Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1e3792e-9cd4-42b6-8b9d-3c2a022a16d6
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ways to Use Message Content to Control Message Processing
There are two types of property promotion: **Distinguished Fields** and **Property Fields**, the latter of which uses property schemas. In BizTalk Editor, you manage both of these types of property promotion by using the **Promote Properties** dialog box, which is accessible by using the **Promote Properties** property of the **Schema** node.  
  
> [!NOTE]
>  There are some restrictions on values that you can promote. For more information, see the table in [Promoting Properties](../core/promoting-properties.md).  
  
 You must decide which type of property promotion to use based on the details of your scenario. Consider the following distinctions between **Distinguished Field** property promotion and **Property Field** property promotion:  
  
- **Distinguished Fields** cannot participate in message routing and therefore they do not appear in the filter expressions. They are only available within the context of an orchestration but they have less overhead when sending and receiving messages.  
  
- **Distinguished Fields** do not have any size limitations. **Property Fields** are limited to 255 characters.  
  
- **Distinguished Fields** do not require any separate artifacts to be created whereas **Property Fields** require the creation and maintenance of a property schema.  
  
  Drawing upon these considerations, you should promote nodes as **Property Fields** only when you intend to use the promoted properties for message routing or tracking purposes. Otherwise, if you are only going to access the promoted properties from within your orchestrations, you should take advantage of the fact that **Distinguished Fields** are much cheaper, more lightweight, and more easy-to-use than **Property Fields**.  
  
  Properties promoted by using the **Distinguished Field** mechanism are only accessible from within orchestrations and cannot be accessed from pipelines, ports, and so on. On the other hand, properties promoted by using the **Property Fields** and property schema mechanism are accessible from all of these components. Another important difference is that property field values are limited to 255 characters and distinguished field values have no such limit.  
  
  This section provides information about these two types of property promotion, including how information about how to establish such promoted properties for a message schema by using BizTalk Editor.  
  
## In This Section  
  
-   [About BizTalk Message Context Properties](../core/about-biztalk-message-context-properties.md)  
  
-   [Instance Message Processing Using Distinguished Fields](../core/instance-message-processing-using-distinguished-fields.md)  
  
-   [Instance Message Processing Using Property Promotion](../core/instance-message-processing-using-property-promotion.md)