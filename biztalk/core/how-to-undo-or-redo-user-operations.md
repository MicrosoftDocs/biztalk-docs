---
title: "How to Undo or Redo User Operations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1cb3708e-a9c2-4795-aba0-9c6d9635e08c
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Undo or Redo User Operations
The support for undo/redo is yet another usability aid provided by the BizTalk Mapper. If you are not satisfied with modifications you have made, or if you have made a change by mistake, you can use undo to gradually come back to an earlier "untouched" state, and resume from there. Redo allows you to reapply the editing actions that have been undone. This topic provides information about the operations that you can undo/redo.  
  
> [!IMPORTANT]
>  You can undo an operation only when you have performed at least one edit operation on the map. Redo is unavailable unless you have used the undo command.  
  
## Prerequisites  
 These instructions require that BizTalk Mapper is running.  
  
## What can you undo/redo?  
 You can undo/redo all editing operations. The operations that can be undone/redone are as follows:  
  
-   Cutting/copying/pasting functoids and/or link  
  
     You cannot undo or redo any number of items (links/functoids) by simply selecting and copying them. Copy function does not change anything on the map.  
  
    > [!NOTE]
    >  For information about how to cut/copy/paste a functoid, see [How to Copy, Cut, and Paste a Functoid](../core/how-to-copy-cut-and-paste-a-functoid.md). For more information about how to cut/copy/paste functoid and link, see [How to Copy, Cut, and Paste Links and Functoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).  
  
-   Linking a source node to a target node, or a source node to a functoid, a functoid to another functoid, or a functoid to a target node  
  
-   Deleting functoids and/or links  
  
-   Moving selected links and functoids to another grid page  
  
-   Adding, moving, reordering, or deleting grid pages  
  
    > [!NOTE]
    >  For information on adding, moving, reordering, or deleting grid pages, see [How to Reorder Grid Pages](../core/how-to-reorder-grid-pages.md).  
  
-   Selecting source and destination schemas while creating a map  
  
-   Replacing source/destination schema  
  
    > [!NOTE]
    >  For information on how to replace source/destination schema, see [How to Replace Schemas](../core/how-to-replace-schemas.md).  
  
-   Configuring input parameters for functoids  
  
    > [!NOTE]
    >  For more information, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).  
  
-   Setting/editing labels for links  
  
    > [!NOTE]
    >  For more information, see [How to Label a Link](../core/how-to-label-a-link.md).  
  
-   Setting/editing labels and/or comments for functoids  
  
    > [!NOTE]
    >  For more information, see [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).  
  
-   Ignore Namespaces for Links and Script Type Precedence properties for Mapper grid.  
  
-   Replacing a link by dragging one end point of a link from a node or functoid to anther node or functoid.  
  
    > [!NOTE]
    >  For more information, see [How to Create Links](../core/how-to-create-links.md).  
  
-   Performing multiple modifications in the **Configure \<Functoid> Functoid** dialog box, which is treated as a single operation.  
  
-   Dragging functoid(s) and/or link(s) within the Mapper grid.  
  
    > [!NOTE]
    >  For more information, see [How to Move a Relationship Between Grid Pages](../core/how-to-move-a-relationship-between-grid-pages.md).  
  
## How can you undo/redo any operation?  
 You can undo/redo an operation in one of the following ways:  
  
-   From the Visual Studio’s **Edit** menu.  
  
-   Clicking the undo and redo icons on the toolbar.  
  
-   Pressing CTRL+Z for undo and CTRL+Y for redo.  
  
## See Also  
 [Working with Grid Pages](../core/working-with-grid-pages.md)