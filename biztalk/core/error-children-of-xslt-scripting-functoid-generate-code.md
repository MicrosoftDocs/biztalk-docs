---
description: "Learn more about: Error - Children of XSLT Scripting Functoid Generate Code"
title: "Error - Children of XSLT Scripting Functoid Generate Code"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.xsltScriptingChildrenGenCode"
---
# Error - Children of XSLT Scripting Functoid Generate Code
**Error Code**  
  
 btm1063  
  
 **Explanation**  
  
 A scenario that contradicts the use of a **Scripting** functoid that is configured to use inline XSLT or an XSLT Call Template was found in the map. In the destination schema, descendent nodes of a node that is linked to the output of such a **Scripting** functoid are attempting to generate XSLT code of their own.  
  
 **User Action**  
  
 Remove the incompatibility by changing the usage of the relevant **Scripting** functoid or changing the child nodes such that they no longer generate XSLT code of their own.
