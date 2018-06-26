---
title: "How to Copy, Cut, and Paste a Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 825847e4-87db-4b40-8e5d-5b5b1c79c6de
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Copy, Cut, and Paste a Functoid
The copy/cut/paste feature in the BizTalk Mapper enables the reusability of functoids. In a map, you can copy, cut, and paste one or more functoids from one grid page to another. This topic provides step-by-step instructions to perform these operations.  
  
 You can use the copy/paste feature when you want to reuse functoids. And, when you want to remove a functoid from the existing location and move it to a new location, you can use the cut/paste feature.  
  
> [!IMPORTANT]
>  When you choose to copy a functoid, the functoid, its label, comments, and the constant-inputs, along with the placeholder indices, are copied. Similarly, when you choose to cut a functoid, the functoid, its label, comments, constant-inputs, along with the placeholder indices, are cut. But, when you paste (after choosing to cut) the selection, only the functoid is retained and the orphaned links are deleted. The label, comments, constant inputs, and placeholder indices are not retained.  
  
 If you select only a functoid, which is either linked to another functoid or a schema node, only the functoid will be cut or copied, without the links. If you cut a functoid that is linked to other functoids in the map or to the schema nodes, the links to the functoid that is cut are deleted.  
  
 You can copy/cut functoids from:  
  
- Within the same grid page of a map  
  
- One grid page to the other in the same map  
  
- One instance of Visual Studio to another  
  
  You can undo or redo the cut and paste operations. For more information, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).  
  
## Prerequisites  
 These instructions require that BizTalk Mapper is running.  
  
### To copy and paste a functoid  
  
1.  In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.  
  
2.  Select the functoid you want to copy. To select multiple functoids, click one functoid, hold down the CTRL key, and then click the other functoids.  
  
    > [!NOTE]
    >  You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s). For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).  
  
3.  Right-click the selection, and then click **Copy**. Alternatively, you can either click **Copy** from the Visual Studio’s **Edit** menu or press CTRL+C on the keyboard.  
  
    > [!NOTE]
    >  For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
4.  Place the cursor where you wish to paste the functoid.  
  
5.  Right-click on the grid page, and then click **Paste**. Alternatively, you can either click **Paste** from the Visual Studio’s **Edit** menu or press CTRL+V on the keyboard. A copy of the selected functoid or group of functoids appears at the new location.  
  
### To cut and paste a functoid  
  
1.  In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.  
  
2.  Select the functoid you want to cut. To select multiple functoids, click one functoid, hold down the CTRL key, and then click the other functoids.  
  
3.  Right-click the selection, and then click **Cut**. Alternatively, you can either click **Cut** from the Visual Studio’s **Edit** menu or press CTRL+X on the keyboard.  
  
    > [!NOTE]
    >  For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
4.  Place the cursor where you wish to paste the functoid.  
  
5.  Right-click on the grid page, and then click **Paste**. Alternatively, you can either click **Paste** from the Visual Studio’s **Edit** menu or press CTRL+V on the keyboard. The selected functoid or group of functoids are deleted from the existing location and appear at the new location.  
  
## See Also  
 [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md)