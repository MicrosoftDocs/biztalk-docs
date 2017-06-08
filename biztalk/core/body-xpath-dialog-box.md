---
title: "Body XPath Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.editor.body.xpath"
helpviewer_keywords: 
  - "Body XPath dialog box [BizTalk Editor]"
  - "BizTalk Editor, Body XPath dialog box"
ms.assetid: 13cfe362-46d7-47c0-ae4f-6d068ffd4859
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Body XPath Dialog Box
Use the **Body XPath** dialog box to provide the XPath to the body of the message associated with enveloped instance messages governed by this schema. The specified XPath indicates the node that serves as the root of the contents (body) of the envelope. Although this content is generally the instance message itself, it can also be a nested envelope.  
  
 The **Body XPath** property can only be set using this dialog box when the **Envelope** property of the **Schema** node is set to **Yes**, indicating that this schema describes an envelope.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Expandable subset of the schema tree**|Expand as necessary to select the node that represents the root node of the document body. The displayed tree is the subset of the schema tree that begins with the root **Record** node for which the **Body XPath** property is being set, and includes all of its descendants.|  
|**Edit box**|Specify the XPath that will be set as the value of the **Body XPath** property if you click **OK**. You can specify this XPath by:<br /><br /> -   Selecting a node in the expandable subset of the schema tree (recommended).<br />-   Typing a custom XPath into the edit box **Note:**  Use caution when manually entering an XPath; its syntax makes it prone to errors.|  
  
## See Also  
 [Envelope Schemas](../core/envelope-schemas.md)   
 [Envelope (Node Property of All Schemas)](../core/envelope-node-property-of-all-schemas.md)