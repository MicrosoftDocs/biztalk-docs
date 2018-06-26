---
title: "How to resize the schema picker, and expand and collapse the schema trees | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 267ea17d-54fe-4031-a044-719606489f24
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to resize the schema picker, and expand and collapse the schema trees
When developing BizTalk maps, you are likely to need to expand and collapse the source and destination schema trees to expose or to hide the various schema nodes. This topic provides step-by-step instructions to resize the schema picker, and to expand and collapse the schema tree.  

## Resize the schema picker

When you create a map, you add a source schema, and a destination schema. When you add or replace a schema, the BizTalk Type Picker window opens, and you select your schema. 

**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can resize this Type Picker window. This feature allows you to see the full name of your schema.

1. In your map, select **Open Destination Schema**, or **Open Source Schema**.
2. In the **BizTalk Type Picker** window, drag the bottom-right corner to increase or decrease the window size.
  
## Expand all or part of a schema tree  
  
1.  Select the node under which you want to completely expand the schema tree.  
  
     The selected node must be a node with a plus (+) or minus (-) icon next to it.  
  
2.  On the **BizTalk** menu, or on the shortcut menu for that node, click **Expand Tree Node**. All nodes below the selected node are completely expanded.  
  
     If the schema tree below the selected node is already completely expanded, the **Expand Tree Node** menu item is disabled.  
  
    > [!NOTE]
    >  Alternatively you can press CTRL+M, E to expand the schema tree nodes. For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
    > [!NOTE]
    >  In a large and complex schema, when you click **Expand Tree Node** on a node that contains complex types, some nodes in the schema may remain in the collapsed state. This is because the recursive process expands only the first occurrence of a given complex type. You must manually expand later occurrences of the same type. This behavior is designed to optimize performance when expanding nodes in large and complex schemas.  
  
## Collapse all or part of a schema tree  
  
1. Select the node under which you want to completely collapse the schema tree.  
  
    The selected node must be a node with a plus (+) or minus (-) icon next to it.  
  
2. On the **BizTalk** menu, or on the shortcut menu for that node, click **Collapse Tree Node**.  
  
    All nodes below the selected node are completely collapsed.  
  
   > [!NOTE]
   >  Alternatively you can press CTRL+M, C to collapse the schema tree nodes. For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
    If the schema tree below the selected node is already collapsed, the **Collapse Tree Node** menu item is disabled.  
  
   This operation will not remember the individual expand and collapse settings of the nodes below the selected node. When you re-expand the collapsed node, previous settings are lost, and you must expand the schema tree below that point node-by-node, or expand it entirely.  
  
### Expand a node
  
- Click the plus (+) icon next to the node you want to expand.  
  
  The selected node is expanded. Whether or not its descendent nodes are expanded or collapsed depends on how the selected node was collapsed and their previous expand and collapse settings.  
  
### Collapse a node
  
- Click the minus (-) icon next to the node you want to collapse.  
  
  The selected node is collapsed.  
  
  This operation will remember the individual expand and collapse settings of the nodes below the selected node. When you re-expand the collapsed node by using the plus (+) icon, the previous individual settings are not lost, and the schema tree below that point returns to its previous state.  
  
## See Also  
 [Using BizTalk Mapper](../core/using-biztalk-mapper.md)