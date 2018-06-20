---
title: "How to Copy, Cut, and Paste Links and Functoids | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80b4792a-5ff6-4603-96cd-b3d3d530c12f
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Copy, Cut, and Paste Links and Functoids
The copy/cut/paste feature in the BizTalk Mapper enables the reusability of a relationship. This topic provides step-by-step instructions to copy, cut, and paste functoids and/or links in a map.  
  
 You can use the copy/paste feature when you want to reuse a set of functoids and/or links. And, when you want to remove the selection from the existing location and move it to a new location, you can use the cut/paste feature.  
  
> [!IMPORTANT]
>  Do you feel cut/paste feature and the move feature are similar? There is a difference. When you select cut, only the functoids and/or links in your selection are removed from the source grid page. But, when you select move, all the functoids and links in the relationship (irrespective of the selection), recursively, are removed from the source grid page. For more information about moving a relationship, see [How to Move a Relationship Between Grid Pages](../core/how-to-move-a-relationship-between-grid-pages.md).  
  
 When you copy/cut a set of functoids and/or links, the functoids, labels, comments, and the constant values (along with the correct place holders) associated with that set are retained.  
  
 You can copy/cut only these map items:  
  
- Link from source to target schema.  
  
- Link from functoid to schema node, if and only if the “functoid” is also selected along with the link.  
  
- Link from functoid to functoid, if and only if both the functoids are selected along with the link.  
  
  You can copy/cut functoids and/or links from:  
  
- Within the same grid page of a map  
  
- One grid page to the other in the same map  
  
- One map to the other in the same instance of Visual Studio  
  
- Across different instances of Visual Studio  
  
  You can undo or redo the cut and paste operations. For more information, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).  
  
  In addition to this, you must consider the following points while pasting links:  
  
- A link between the source and target schema can be pasted if and only if the current map, where the link is being pasted, contains a source node as well as a target node whose XPath is identical to the XPath of the source and target nodes for the link being pasted.  
  
- A link between the source and target schema can be pasted if and only if there is no existing link between the aforesaid source and target nodes.  
  
- A link from a functoid to target schema can be pasted if and only if there exists a target node whose XPath is same as the XPath of the target node of the link being pasted.  
  
- A link from a source schema to a functoid can be pasted if and only if there exists a source node whose XPath is same as the XPath of the source node of the link being pasted.  
  
> [!NOTE]
>  When you select multiple items (links and/or functoids) such that some of them cannot be cut/copied, then on executing the cut/copy command, the status bar in Visual Studio displays a warning message “Some of the selected items could not be cut/copied.” The message also displays relevant details.  
  
## Prerequisites  
 These instructions require that BizTalk Mapper is running.  
  
### To copy and paste a relationship  
  
1.  In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.  
  
2.  Select the functoids and/or links you want to copy.  
  
    > [!TIP]
    >  You can select either by holding down the CTRL key, and then selecting the desired functoids and/or links or by dragging and dropping the mouse across the links to form a rectangular selection.  
  
    > [!NOTE]
    >  You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s). For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).  
  
3.  Right-click the selection. and then click **Copy**. Alternatively, you can press CTRL+C on the keyboard.  
  
    > [!NOTE]
    >  For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
4.  Place the cursor where you wish to paste the selection.  
  
5.  Right-click on the grid page, and then click **Paste**. Alternatively, you can select and press CTRL+V on the keyboard. A copy of the selection appears at the new location.  
  
### To cut and paste a relationship  
  
1.  In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.  
  
2.  Select the functoids and/or links you want to cut.  
  
    > [!TIP]
    >  You can select either by holding down the CTRL key, and then selecting the desired functoids and/or links or by dragging and dropping the mouse across the links to form a rectangular selection.  
  
    > [!NOTE]
    >  You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s). For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).  
  
3.  Right-click the selection, and then click **Cut**. Alternatively, you can press CTRL+X on the keyboard.  
  
    > [!NOTE]
    >  For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
4.  Place the cursor where you wish to paste the selection.  
  
5.  Right-click on the grid page, and then click **Paste**. Alternatively, you can select and press CTRL+V on the keyboard. The selection is deleted from the existing location and appears at the new location.