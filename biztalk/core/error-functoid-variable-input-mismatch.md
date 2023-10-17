---
description: "Learn more about: Error - Functoid Variable Input Mismatch"
title: "Error - Functoid Variable Input Mismatch"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.functoidVariableInputMismatch"
---
# Error - Functoid Variable Input Mismatch
**Error Code**  

 btm1011  

 **Explanation**  

 The indicated functoid does not have the correct number of input parameters specified. The number of input parameters must be in the specified range.  

 **User Action**  

 Use one or more of the following methods to provide the indicated number of input parameters to the indicated functoid, paying particular attention to the expected order of input parameters:  

- To create additional links, drag to create links between the indicated functoid and either nodes in the source schema or the output of other functoids that are located to the left of the indicated functoid in a map grid page.  

- To create additional links, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then configure and rearrange the order of the input parameters in the **Configure \<Functoid\> Functoid** dialog box. Constant input parameters can be created, given values, and put in the proper order relative to the other input parameters in this dialog box.  

- To remove existing links, for each link connected to the left side of the indicated functoid, right-click the link and then click **Delete**.  

- To remove existing links, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid\> Functoid** dialog box, delete all input parameters by selecting and clicking the ![Icon for deleting all input parameters.](../core/media/bts-tls-paramdelete.gif) button for each of them. You must use this method to delete constant input parameters.
