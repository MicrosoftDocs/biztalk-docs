---
title: "How to Manage the XSD View | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3245ebf0-6128-47b4-8e88-ea06ececbc15
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Manage the XSD View
Management tasks with respect to the XSD view can be divided into three categories: changing its size, changing its background color and font, and changing its refresh characteristics.  
  
 The latter category, concerning refresh characteristics, is most useful when working with large schemas, for which using automatic refresh might cause undesirable delays. In such cases, you can disable automatic (continuous) refresh, and instead refresh the XSD view manually as needed.  
  
 This topic provides step-by-step instructions for these tasks.  
  
### To make the XSD view taller or shorter  
  
1. Move the mouse pointer to the bottom edge of the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] main editing window, which displays the XSD view side-by-side with the schema tree view, until the cursor changes to the standard window vertical resizing icon.  
  
2. Click and hold the left mouse button and drag the window edge either up or down.  
  
    You have vertically resized the XSD view by vertically resizing the entire main editing window.  
  
### To make the XSD view wider or more narrow  
  
1. Move the mouse pointer to the pane divider in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] main editing window, which divides the XSD view from the schema tree view, until the cursor changes to the standard window horizontal resizing icon.  
  
2. Click and hold the left mouse button and drag the pane edge either left (wider) or right (narrower).  
  
    You have horizontally resized the XSD view by changing the amount of the main editing window dedicated to the XSD view, relative to the schema tree view.  
  
    You can also make the XSD view wider or narrower by horizontally resizing the entire main editing window.  
  
### To change the background color and/or font used by the XSD view  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **Tools** menu, click **Options**.  
  
2. In the **Options** dialog box, click the BizTalk Editor folder, and if necessary, expand the **Schema Display** category by clicking the plus (+) icon.  
  
3. Change the background color and/or font by using the drop-down color picker and/or **Font** dialog box associated with the **XSD View Background Color** and **XSD View Font** properties, respectively.  
  
    Access the **Font** dialog box by using the ellipsis (**…**) button located at the right end of the **XSD View Font** property value box.  
  
### To turn automatic refresh of the XSD view on and off  
  
-   In BizTalk Editor, below the **XSD** tab, click **Turn off auto refresh** or **Turn on auto refresh**.  
  
     When auto-refresh is off, the XSD view is blank.  
  
    > [!IMPORTANT]
    >  By default, auto-refresh is on. As your schemas become bigger and bigger, it becomes increasingly important for you to turn off the automatic refresh feature and refresh your schema manually as needed.  
  
### To manually refresh the XSD view  
  
-   On the **BizTalk** menu, click **Refresh XSD**.  
  
     The XSD view updates to reflect any changes you have made to the schema tree.  
  
    > [!NOTE]
    >  You can also manually refresh the XSD view by clicking **Refresh XSD** on the shortcut menu associated with every node in the schema tree, or by clicking the **Refresh** link below the **XSD** tab in the XSD view.  
  
## See Also  
 [Using BizTalk Editor](../core/using-biztalk-editor.md)