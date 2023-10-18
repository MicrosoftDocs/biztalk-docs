---
description: "Learn more about: Warning - Body XPath Not A Descendent"
title: "Warning - Body XPath Not A Descendent"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.bodyXPathNotDescendant"
---
# Warning - Body XPath Not A Descendent
**Error Code**  
  
 BEC1004  
  
 **Explanation**  
  
 The **Body XPath** property of the indicated root node in this envelope schema references a node that is not a descendent of that root node, as required. This error should not occur unless the **Body XPath** property is modified outside of BizTalk Editor.  
  
 **User Action**  
  
 Select the indicated root node and select the value for the **Body XPath** property that correctly identifies the top-level node of the associated message body.
