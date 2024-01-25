---
description: "Learn more about: How to Move and Copy Nodes"
title: "How to Move and Copy Nodes"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Move and Copy Nodes
You will probably encounter situations where you want to move an existing node to a different location in the schema tree. You might also be able to save time by making a copy of an existing node and then pasting it into a different location in the schema tree. This topic provides step-by-step instructions for performing these tasks.  
  
> [!NOTE]
>  BizTalk Editor supports copying and pasting nodes only within schemas, not between schemas.  
  
### To move a node within a schema  
  
1.  If necessary, expand the schema tree to show both the node you are moving and the location to which you want to move it. For more information about expanding and collapsing the schema tree view, see [Managing the Schema Tree View](../core/how-to-manage-the-schema-tree-view.md).  
  
2.  Click and hold the node that you want to move and drag it to another location in the tree.  
  
> [!NOTE]
>  When you begin to drag the node up and down the schema tree, the mouse pointer changes to an Up, Down, or child arrow. This arrow indicates where the node will be placed when you release the mouse button, either before the node, after the node, or as a child of the node.  
  
#### To copy a node within a schema  
  
1.  Right-click the node that you want to copy, and then click **Copy**.  
  
2.  Right-click the **Record** node or group node into which you want to insert the copied node, and then click **Paste**.  
  
     The copy of the copied node is placed at the end of the child nodes of the **Record** node or group node you selected in step 2.  
  
> [!NOTE]
>  You may only use cut/copy/paste functionality within a single schema. In other words, you cannot copy nodes from one schema into another schema.  
  
## See Also  
 [Working with Existing Nodes](../core/working-with-existing-nodes.md)
