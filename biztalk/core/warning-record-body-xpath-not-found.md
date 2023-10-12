---
description: "Learn more about: Warning - Record Body XPath Not Found"
title: "Warning - Record Body XPath Not Found"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.recordBodyXPathNotFound"
---
# Warning - Record Body XPath Not Found
**Error Code**  
  
 BEC1008  
  
 **Explanation**  
  
 The **Body XPath** property of the indicated root node in this envelope schema was found to be empty or referencing a nonexistent node. Envelope schemas, as specified by the **Envelope** property of the **Schema** node, are required to have a valid value in the **Body XPath** property of the specified root reference node in the schema.  
  
 If no root reference node is specified by the **Root Reference** property of the **Schema** node, the first root node in the schema, the default root reference node, is required to have a valid value in its **Body XPath** property. **Body XPath** property values are used to identify the schema for the each of the messages contained within the envelope.  
  
 **User Action**  
  
 Select the indicated root node and then select the value for the **Body XPath** property that correctly identifies the schema of the associated message body.
