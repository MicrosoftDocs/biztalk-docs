---
title: "How to Add Looping Functoids to a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b24051b7-3e79-4a49-8249-a057c048ddae
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Looping Functoids to a Map

## Overview
The **Looping** functoid combines multiple records or fields in the source schema into a single record in the destination schema.  

 For conceptual information about the **Looping** functoid, see [Looping Functoid](../core/looping-functoid.md).  

 Under certain conditions, some functoids might not behave as expected when they are used in a map with a **Looping** functoid. If such a functoid meets the following conditions, it does not produce the expected results:  

-   The functoid has more than one input link.  

-   Two or more of the functoid input links are linked to child fields of the input records to the **Looping** functoid, where the child fields are not siblings.  

-   The functoid has an output link that is linked to a child field of the output record of the **Looping** functoid.  

## Add the Looping functoid to a map and configure it  

1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.  

    The list of advanced functoids in the chosen category appears.  

2. Drag the **Looping** functoid from the Toolbox to the appropriate location on a grid page.  

    ![](../core/media/bts-tls-looping.gif "bts_tls_looping")  
   Looping functoid  

   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display that other grid page first.  
   > 
   >  If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement. Functoids are executed from left to right. The output of a functoid can only be input to another functoid that is farther to the right.  

3. To establish the input parameters for the **Looping** functoid, create an input link by dragging a record or field from the source schema to the **Looping** functoid, or dragging the **Looping** functoid to a record or field in the source schema. Repeat as required to include all of the relevant input records or fields to the **Looping** functoid.  

4. To use the output parameter from the **Looping** functoid, create an output link by dragging the **Looping** functoid to a record or field in the destination schema, or by dragging a record or field in the destination schema to the **Looping** functoid.  

   > [!NOTE]
   >  Unlike many other functoids, the output of the **Looping** functoid can only be linked to an element of the destination schema.  

## See Also  
- [Adding Advanced Functoids to a Map](../core/adding-advanced-functoids-to-a-map.md)   
- **Looping Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
