---
description: "Learn more about: Optional Nodes"
title: "Optional Nodes"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Optional Nodes
Using optional nodes will produce a warning when you test your map. There are two conditions in which a source node may be considered optional:  
  
- The actual record or field is optional.  
  
- The source record or field is required, but a parent, grandparent, and farther up the hierarchy is optional.  
  
  You may have situations when you have records and fields in a source schema that are optional, but the destination schema requires the corresponding records or fields.  
  
  In both of the possible conditions, testing your map produces a warning in the **Output** window. In addition, the output data will not include the target node.  
  
## See Also  
 [Testing Maps](../core/testing-maps.md)
