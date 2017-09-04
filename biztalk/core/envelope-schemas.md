---
title: "Envelope Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af296c30-95dc-4fef-9aa3-bea2f2cd8caf
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Envelope Schemas

## Overview
You can create an envelope schema in all of the same ways that you can create an XML schema for a business document. You can create a schema from a well-formed XML envelope instance message, or from Document Type Definition (DTD) or XML-Data reduced (XDR) representations of the envelope schema. Or, you can create a new schema, either in conjunction with other schemas or not. Because envelope schemas are generally much smaller and less complicated than most business document schemas, creating new envelope schemas is usually a viable alternative.  
  
 To define a schema as an envelope schema, you need to set the **Envelope** property of the **Schema** node to the value **Yes**. When you define an envelope schema, you should point the envelope's **Body XPath** to the parent node that contains only the \<any> child element. In order for the XML assembler to use the envelope, the parent node must not contain any other elements.  
  
 When you set **Envelope** property to **Yes**, it means that the actual message content of the XML instance message (called the body of the message) is present somewhere inside the root **Record** node of this schema, as specified by the **Body XPath** property of that node. Therefore, you must also set additional properties based on a variety of conditions:  
  
-   If an envelope schema has a single root, you must set the **Body XPath** property for that root.  
  
-   If an envelope schema has multiple roots and the **Root Reference** property is not set, you must set the **Body XPath** property for all roots.  
  
-   If an envelope schema has multiple roots and the **Root Reference** property is set, you must set the **Body XPath** property of the corresponding root **Record** node. You can optionally set the **Body XPath** property for the remaining roots.  
  
-   Regardless of whether an envelope schema has a single root or multiple roots, setting the **[Root Reference** property is not required.  

More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## See Also  
 [Different Types of BizTalk Schemas](../core/different-types-of-biztalk-schemas.md)   
 [How to Create Schemas for Envelopes](../core/how-to-create-schemas-for-envelopes.md)