---
title: "How to Add Value Mapping Functoids to a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc70067a-67a1-4a0e-95e5-b0cb327d2cee
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Value Mapping Functoids to a Map
The **Value Mapping** functoid returns the value of its second parameter if its first parameter is true. A common use of the functoid is to change the attributes of a field into the attributes of a record.  
  
 For conceptual information about the **Value Mapping** functoid, see [Value Mapping Functoid](../core/value-mapping-functoid.md).  
  
### To add the Value Mapping functoid to a map and configure it  
  
1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.  
  
    The list of advanced functoids in the chosen category appears.  
  
2. Drag the **Value Mapping** functoid (![](../core/media/bts-tls-valmap.gif "bts_tls_valmap")) from the Toolbox to the appropriate location on a grid page.  
  
   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display that other grid page first.  
  
   > [!NOTE]
   >  If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement. Functoids are executed from left to right. The output of a functoid can only be input to another functoid that is farther to the right.  
  
3. To establish the first input parameter for the **Value Mapping** functoid, create an input link by dragging the **Value Mapping** functoid to a record or field node in the source schema, or to another functoid to its left, that has a Boolean data type and that will produce an input value of "true" or "false".  
  
   > [!NOTE]
   >  You can also drag in the opposite direction, dragging the source of the Boolean value to the **Value Mapping** functoid.  
  
4. To establish the second input parameter for the **Value Mapping** functoid, create an input link by dragging the **Value Mapping** functoid to a record or field node in the source schema, or by dragging a record or field node in the source schema to the **Value Mapping** functoid.  
  
   > [!NOTE]
   >  The second input parameter to the **Value Mapping** functoid can also be from the output of another functoid to its left. Create the links that represent such sources of input by dragging one of the relevant functoids to the other relevant functoid.  
  
5. To use the output parameter from the **Value Mapping** functoid, create an output link by dragging the **Value Mapping** functoid to a record or field in the destination schema, or by dragging a record field in the destination schema to the **Value Mapping** functoid.  
  
   > [!NOTE]
   >  As with other functoids, the output of the **Value Mapping** functoid can serve as input to another functoid.  
  
## See Also  
 [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)