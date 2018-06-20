---
title: "How to Add Iteration Functoids to a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1eaea929-e352-447d-b119-bd69b6b24e6c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Iteration Functoids to a Map
The **Iteration** functoid outputs the index of the current record in a looping structure, beginning at 1 for the first record, 2 for the second record, and so on.  
  
 For conceptual information about the **Iteration** functoid, see [Iteration Functoid](../core/iteration-functoid.md).  
  
### To add the Index functoid to a map and configure it  
  
1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.  
  
    The list of advanced functoids in the chosen category appears.  
  
2. Drag the **Index** functoid (![](../core/media/bts-tls-iteration.gif "bts_tls_iteration")) from the Toolbox to the appropriate location on a grid page.  
  
   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display that other grid page first.  
  
   > [!NOTE]
   >  If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement. Functoids are executed from left to right. The output of a functoid can only be input to another functoid that is farther to the right.  
  
3. To establish the looping record input parameter for the **Iteration** functoid, create an input link by dragging a looping record from the source schema to the **Iteration** functoid, or by dragging the **Iteration** functoid to a looping record in the source schema.  
  
4. To use the output parameter from the **Iteration** functoid, create an output link by dragging the **Iteration** functoid to a field in the destination schema, or by dragging a field in the destination schema to the **Iteration** functoid.  
  
   > [!NOTE]
   >  The data type of the relevant field in the destination schema must be numeric or convertible to numeric so that it matches the output data type of the **Iteration** functoid.  
  
## See Also  
 [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)