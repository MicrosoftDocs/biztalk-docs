---
title: "Assert Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e91dac06-f909-4fb2-8c87-828a3dfe2c27
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Assert Functoid
The **Assert** functoid either outputs a string value or throws an exception based on a Boolean value. If you combine this functoid with one or more of the **Logical** functoids, you can effectively test assumptions about conditions in your map. For example, if you have a map that expects purchase order amounts never to exceed a certain threshold, you can test the purchase order value by using the **Greater Than** functoid and then connect it to the **Assert** functoid. If the logical functoid returns **True**, the **Assert** functoid will throw an exception using a string you provide.  
  
 ![Assert Functoid](../core/media/assertfunctoid.gif "AssertFunctoid")  
  
## See Also  
 [Assert Functoid Reference](../core/assert-functoid-reference.md)   
 [Logical Functoids Reference](../core/logical-functoids-reference.md)