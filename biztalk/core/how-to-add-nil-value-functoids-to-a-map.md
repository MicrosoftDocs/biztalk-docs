---
title: "How to Add Nil Value Functoids to a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2e193ed-fe5c-4b12-aab8-ff2d81fd45e1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Nil Value Functoids to a Map
The **Nil Value** functoid sets the value of the destination node to **Nil**.  

 For conceptual information about the **Nil Value** functoid, see [Nil Value Functoid](../core/nil-value-functoid.md).  

## Add the Nil Value functoid to a map and configure it  

1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids. The list of advanced functoids in the chosen category appears.  

2. Drag the **Nil Value** functoid (![Nil Value functoid](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid")) from the Toolbox to the appropriate location on a grid page.  

   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display that other grid page first.  
   >
   >  If you are constructing a map that uses more than one functoid, you need to consider their relative left-to-right placement. Functoids are executed from left to right. The output of a functoid can only be input to another functoid that is farther to the right.  

3. The **Nil Value** functoid can have zero to one input parameters. If there is no input parameter for this functoid, the target node is set to **Nil**. To establish the input parameter for the **Nil Value** functoid, create an input link by dragging the output from some other **Logical** functoid or from a variable Boolean field in the input instance message.  

4. To use the output parameter from the **Nil Value** functoid, create an output link by dragging the **Nil Value** functoid to a record or field in the destination schema.  

   > [!NOTE]
   >  As with other functoids, the output of the **Nil Value** functoid can be used as input to another functoid.  

## See Also  
- **Nil Value Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
- [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)
