---
description: "Learn more about: Error - Index Functoid Has No Index"
title: "Error - Index Functoid Has No Index"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.indexFunctoidHasNoIndex"
---
# Error - Index Functoid Has No Index
**Error Code**  
  
 btm1014  
  
 **Explanation**  
  
 No index value(s) have been provided for the indicated **Index** functoid.  
  
 **User Action**  
  
 Provide an appropriate number of index input parameters for the indicated **Index** functoid, where the appropriate number is determined by the number of looping **Record** nodes within which the **Field** node in the source schema is nested. To created index input parameters, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then use the ![Icon for deleting all input parameters.](../core/media/bts-tls-paraminsert.gif) button within the **Configure \<Functoid\> Functoid** dialog box to add one or more constant input parameters, where the first one represents an index into the immediate parent looping **Record** node, and subsequent index input parameters represent increasingly remote ancestor looping **Record** nodes.
