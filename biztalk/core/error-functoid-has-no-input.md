---
description: "Learn more about: Error - Functoid Has No Input"
title: "Error - Functoid Has No Input"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.functiodHasNoInput"
---
# Error - Functoid Has No Input
**Error Code**  

 btm1012  

 **Explanation**  

 The indicated functoid requires at least one input parameter, but no input parameters have been specified.  

 **User Action**  

 Use one or both of the following methods to provide the appropriate number of input parameters to the indicated functoid, paying particular attention to the expected order of input parameters:  

- Drag to create links between the indicated functoid and either nodes in the source schema or the output of other functoids that are located to the left of the indicated functoid in a map grid page.  

- Select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then configure and rearrange the order of the input parameters in the **Configure \<Functoid\> Functoid** dialog box. Constant input parameters can be created, given values, and put in the proper order relative to the other input parameters in this dialog box.
