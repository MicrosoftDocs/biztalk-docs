---
description: "Learn more about: Error - First Input to Index Functoid Not Valid"
title: "Error - First Input to Index Functoid Not Valid"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.firstInputToIndexNotValid"
---
# Error - First Input to Index Functoid Not Valid
**Error Code**  
  
 btm1015  
  
 **Explanation**  
  
 The first input parameter to the indicated **Index** functoid is not from a **Field** node within a looping **Record** node in the source schema.  
  
 **User Action**  
  
 Create the appropriate input link by dragging between a **Field** node within a looping **Record** node in the source schema and the indicated **Index** functoid. It may be necessary to open the **Configure \<Functoid\> Functoid** dialog box by selecting the indicated **Index** functoid and clicking the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window in order to ensure that the newly created link is the first input parameter to the indicated **Index** functoid.
