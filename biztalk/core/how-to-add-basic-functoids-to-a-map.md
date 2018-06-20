---
title: "How to Add Basic Functoids to a Map | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a81fb73-cccf-4f74-af92-39e4af13e255
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Basic Functoids to a Map
Many functoids are very simple to use. These are referred to here as basic functoids to distinguish them from the functoids in the **Advanced** category. Basic functoids comprise the remaining categories of functoids such as Conversion, Cumulative, Database, Date and Time, Logical, Mathematical, Scientific, and String.  
  
 Basic functoids, in general, have simple types, such as numbers and strings, as their input and output links.  
  
 Using a basic functoid involves adding it to a grid page, creating input links to the functoid, coming from the left, and creating output link from the functoid, leaving to the right. This topic provides step-by-step instructions for these operations.  
  
## Add a basic functoid to a map  
  
1. With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the appropriate tab to select the category of the functoid you want to use.  
  
    The list of available functoids in the chosen category appears.  
  
2. Drag the functoid you want to use from the Toolbox to the appropriate location on a grid page.  
  
   > [!NOTE]
   >  The functoid will be placed on the displayed grid page. If you want to put the functoid onto a different grid page, you need to display that other grid page first.  
  
   > [!NOTE]
   >  If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement. Functoids are executed from left to right. The output of a functoid can only be input to another functoid that is farther to the right.  
  
## Create input links to a basic functoid  
  
1. Drag a record or field node from the source schema to the basic functoid in the displayed grid page.  
  
    **- Or -**  
  
    In the displayed grid page, drag another functoid, which is located farther to the left, to the basic functoid to which you want to create an input link.  
  
    **- Or -**  
  
    Drag the basic functoid in the displayed grid page to a record or field node in the source schema.  
  
    **- Or -**  
  
    In the displayed grid page, drag the basic functoid to which you want to create an input link to another functoid that is located farther to the left.  
  
   > [!NOTE]
   >  While dragging, the moving endpoint of the link, as opposed to the anchored endpoint of the link, changes to a crosshair icon to allow more accurate targeting of the second endpoint. If you hover the moving endpoint of the link over an object that is not an appropriate second endpoint for the link, such as might occur when there is a data type mismatch, the crosshair icon changes to an icon showing a circle with a diagonal slash through it.  
  
2. Repeat step 1 as necessary to establish the complete set of input links (though perhaps not the entire set of input parameters) to the basic functoid.  
  
   > [!NOTE]
   >  There are a few functoids that do not require any input links. For example, the **Date**, **Time**, and **Date and Time** functoids in the **Date and Time** functoid category provide the current date, time, or date and time, respectively, at which an instance message is being processed. Thus, they do not require any input parameters from the source schema.  
   > 
   > [!NOTE]
   >  The order of input parameters to many functoids is significant, as indicated in the corresponding functoid reference topic (see **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]). The order in which you create links sets the order of input parameters to the functoid. For more information about functoid properties and specifying the order of functoid input parameters, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md). For information about how to configure the input parameters of a functoid, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).  
   > 
   > [!NOTE]
   >  Ensure the functoids or source schema node you want to link are visible in the displayed grid page or source schema window before you begin linking.  
  
## Create the output link from a basic functoid  
  
1.  Drag a record or field node from the destination schema to the basic functoid in the displayed grid page.  
  
     **- Or -**  
  
     In the displayed grid page, drag another functoid, which is located farther to the right, to the basic functoid to which you want to create the output link.  
  
     **- Or -**  
  
     Drag the basic functoid in the displayed grid page to a record or field node in the destination schema.  
  
     **- Or -**  
  
2.  In the displayed grid page, drag the basic functoid to which you want to create the output link to another functoid that is located farther to the right.  
  
    > [!NOTE]
    >  Ensure the functoids and source schema node that you want to link are already visible in the displayed grid page and source schema window, respectively, before you begin the linking operation.  
  
    > [!NOTE]
    >  Functoid linking always attempts to disallow inappropriate linking, such as links where source and target data types do not match.  
  
    > [!NOTE]
    >  While dragging, the moving end point of the link, as opposed to the anchored endpoint of the link, changes to a crosshair icon to allow more accurate targeting of the second endpoint. If you hover the moving endpoint of the link over an object that is not an appropriate second endpoint for the link, such as might occur when there is a data type mismatch, the crosshair icon changes to an icon showing a circle with a diagonal slash through it.  
  
## See Also  
**Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]