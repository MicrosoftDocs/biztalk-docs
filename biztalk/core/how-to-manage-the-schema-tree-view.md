---
title: "How to Manage the Schema Tree View | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97fb7a88-e38a-4abb-93bc-a5be1bd091e6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Manage the Schema Tree View
Management tasks with respect to the schema tree view can be divided into four categories: changing its size, changing its background color and font, changing its use of warning dialogs, and expanding and collapsing its tree structure. This topic provides step-by-step instructions for these various tasks.  
  
### To make the schema tree view taller or shorter  
  
1. Move the mouse pointer to the bottom edge of the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] main editing window, which displays the schema tree view side-by-side with the XSD view, until the cursor changes to the standard window vertical resizing icon.  
  
2. Click and hold the left mouse button and drag the window edge either up or down.  
  
    You have vertically resized the schema tree view by vertically resizing the entire main editing window.  
  
### To make the schema tree view wider or more narrow  
  
1. Move the mouse pointer to the pane divider in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] main editing window, which divides the schema tree view from the XSD view, until the cursor changes to the standard window horizontal resizing icon.  
  
2. Click and hold the left mouse button and drag the pane edge either left (narrower) or right (wider).  
  
    You have horizontally resized the schema tree view by changing the amount of the main editing window dedicated to the schema tree view, relative to the XSD view.  
  
    You can also make the schema tree view wider or narrower by horizontally resizing the entire main editing window.  
  
### To change the background color and/or font used by the schema tree view  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **Tools** menu, click **Options**.  
  
2. In the **Options** dialog box, click the BizTalk Editor folder, and if necessary, expand the **Schema Display** category by clicking the plus (+) icon.  
  
3. Change the background color and/or font by using the drop-down color picker and/or **Font** dialog box associated with the **Schema Tree Background Color** and **Schema Tree Font** properties, respectively.  
  
    Access the **Font** dialog box by using the ellipsis (**…**) button located at the right end of the **Schema Tree Font** property value box.  
  
### To change the warning dialogs used when working in the schema tree view  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **Tools** menu, click **Options**.  
  
2. In the **Options** dialog box, click the **BizTalk Editor** folder, and if necessary, expand the **Editing Options** section by clicking the plus (+) icon.  
  
3. Set any of the following properties to **True** or **False** by using the drop-down list accessed at the right edge of the respective property value box.  
  
   > [!NOTE]
   >  The value **True** is the default value for all three warning dialog box options.  
  
   |Property|Description|  
   |--------------|-----------------|  
   |**Show Destroy Structure Warning Dialog**|When set to **True**, displays a warning dialog box before the schema structure is destroyed, and allows you to cancel the destructive operation.|  
   |**Show Encode Warning Dialog**|When set to **True**, displays a dialog box when the node name you have typed will not be valid in XML unless encoded, allowing you to cancel the naming operation, or proceed with encoding the name.|  
   |**Show Invalid Insert Dialog**|When set to **True**, displays a warning dialog box for certain node insertion errors, and offers options about how to proceed. The possible node insertion errors include:<br /><br /> -   You have created duplicate **Field Attribute** nodes with the same name and the same parent node.<br />-   You have created duplicate **Record** nodes with the same name and the same parent node, but with different underlying types.|  
  
### To completely expand all or part of the schema tree  
  
-   Select the node under which you want to completely expand the schema tree.  
  
     The selected node must be a node with a plus (+) or minus (-) icon next to it.  
  
     On the **BizTalk** menu, or on the shortcut menu for that node, click **Expand Schema Node**. All nodes below the selected node are completely expanded. If the schema tree below the selected node is already completely expanded, the **Expand Schema Node** menu item will be dimmed.  
  
    > [!NOTE]
    >  In a large and complex schema, when you click **Expand Schema Node** on a node that contains complex types, some nodes in the schema may remain in the collapsed state. This is because the recursive process expands only the first occurrence of a given complex type. You must manually expand later occurrences of the same type. This behavior is designed to optimize performance when expanding nodes in large and complex schemas.  
  
### To completely collapse all or part of the schema tree  
  
1.  Select the node under which you want to completely collapse the schema tree.  
  
     The selected node must be a node with a plus (+) or minus (-) icon next to it.  
  
2.  On the **BizTalk** menu, or on the shortcut menu for that node, click **Collapse Schema Node**.  
  
     All nodes below the selected node are completely collapsed.  
  
    > [!NOTE]
    >  If the schema tree below the selected node is already collapsed, the **Collapse Schema Node** menu item will be dimmed.  
  
    > [!NOTE]
    >  This operation will not remember the individual expand and collapse settings of the nodes below the selected node. In other words, when you re-expand the collapsed node, previous individual settings are lost and you must expand the schema tree below that point node-by-node, or expand it entirely.  
  
### To expand a node of the schema tree  
  
-   Click the plus (+) icon next to the node you want to expand.  
  
    > [!NOTE]
    >  The chosen node is expanded. Whether or not its descendent nodes are expanded or collapsed depends on how the chosen node was collapsed and their previous expand and collapse settings.  
  
### To collapse a node of the schema tree  
  
-   Click the minus (-) icon next to the node you want to collapse.  
  
    > [!NOTE]
    >  The chosen node is collapsed.  
  
    > [!NOTE]
    >  This operation will remember the individual expand and collapse settings of the nodes below the chosen node. In other words, when you re-expand the collapsed node by using the plus (+) icon, the previous individual settings are not lost and the schema tree below that point returns to its previous expand/collapse state.  
  
## See Also  
 [Using BizTalk Editor](../core/using-biztalk-editor.md)