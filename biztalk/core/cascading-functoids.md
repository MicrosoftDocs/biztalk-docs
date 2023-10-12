---
description: "Learn more about: Cascading Functoids"
title: "Cascading Functoids"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Cascading Functoids
Functoids are said to be cascaded when one functoid is linked to another functoid before it is linked to a record or field in the destination schema. For example, you can create cascading functoids in which two concatenated strings produce a third string fed into a field in the destination schema.  
  
 When you cascade functoids, you can create multiple, consecutive transformations in the grid page. While there is no limit to the number of functoids that you can cascade in a page, use cascading wisely. Complex cascading can increase the time to transform an input instance message into an output instance message, significantly reducing run time performance.  
  
## See Also  
 [Functoids in Maps](../core/functoids-in-maps.md)   
 [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md)
