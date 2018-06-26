---
title: "How to Add Assert Functoids to a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ccdd79a2-b70f-489b-8711-e00a50d8e2d8
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Assert Functoids to a Map
The **Assert** functoid enables you to test your assumptions about conditions in your map. For example, if you perform some calculations to determine an additional discount on product purchases, you might assert that the additional discount be no more than $100 by using a logical functoid (**Greater Than** or **Less Than**).  

> [!NOTE]
>  The **Assert** functoid only fires in development builds or when the **Generate Debugging Information** property in the project build settings is set to **True**. When your BizTalk application is compiled for deployment and the **Generate Debugging Information** property is set to **False** (the default), assertions are ignored.  

 For conceptual information about the **Assert** functoid, see [Assert Functoid](../core/assert-functoid.md).  

## Add the Assert functoid to a map and configure it  

1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids. The list of advanced functoids in the chosen category appears.  

2. Drag the **Assert** functoid (![Assert functoid](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid")) from the Toolbox to the appropriate location on a grid page.  

   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display that other grid page first. 
   >    
   >  If you are constructing a map that uses more than one functoid, you need to consider their relative left-to-right placement. Functoids are executed from left to right. The output of a functoid can only be input to another functoid that is farther to the right.  

3. The functoid must have exactly three input parameters and it generates one output parameter. To establish the first parameter for the **Assert** functoid, create an input link by dragging the output from some other **Logical** functoid or from a variable Boolean field in the input instance message.  

4. To establish the second input parameter for the **Assert** functoid, create an input link by a field node in the source schema to the **Assert** functoid, or insert a constant.  

5. To establish the third input parameter for the **Assert** functoid, create an input link by a field node in the source schema to the **Assert** functoid, or insert a constant.  

6. To use the output parameter from the **Assert** functoid, create an output link by dragging the **Assert** functoid to a field in the destination schema.  

   > [!NOTE]
   >  As with other functoids, the output of the **Assert** functoid can be used as input to another functoid.  

## See Also  
- **Assert Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
- [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)
