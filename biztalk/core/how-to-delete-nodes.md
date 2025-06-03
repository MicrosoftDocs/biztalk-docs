---
description: "Learn more about: How to Delete Nodes"
title: "How to Delete Nodes"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Delete Nodes
There will be times when you want to delete a node in the schema tree. This topic provides step-by-step instructions for this task.  
  
### To delete a node  
  
1.  Right-click the node that you want to delete, and then click **Delete**.  
  
2.  Click **Yes** in the confirmation dialog box.  
  
> [!CAUTION]
>  When you delete a **Record** node, all of its child nodes are also deleted.  
  
> [!CAUTION]
>  If you delete a node that has a reference to it elsewhere in the schema tree, the referencing node will also be deleted.  
  
> [!NOTE]
>  If a node is dimmed, it is read-only and you cannot delete it.  
  
## See Also  
 [Working with Existing Nodes](../core/working-with-existing-nodes.md)
