---
title: "How to Manage Existing Links | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0db213b9-df84-4ebd-a59f-7691774d5031
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Manage Existing Links
Sometimes you may need to change the source or destination of a link, name or rename a link, or delete a link. This topic provides step-by-step instructions for performing these types of link operations.  
  
### To change the source or destination of a link  
  
1.  In BizTalk Mapper, in a grid page, click a link to select it.  
  
     The endpoints of a selected link in the grid page are highlighted.  
  
2.  Drag either endpoint of the link to the new schema node or functoid to which you want it to connect it.  
  
     As you drag an endpoint, the cursor becomes a crosshair. If you point to a schema node or functoid (or other object) which cannot accept the link, the cursor becomes a circle with a line through it.  
  
    > [!IMPORTANT]
    >  If you have two or more input links connected to a functoid and you redirect one or more of those input links to other nodes in the source schema or to other functoids, the order of the input parameters to the original functoid may not be preserved. Use the **Configure \<Functoid\> Functoid** dialog box to review the resulting order of the input parameters and to reorder them if necessary. For more information about reordering the input parameters of a functoid, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md).  
  
### To set/edit the label of a link  
  
1. In BizTalk Mapper, in a grid page, click a link to select it.  
  
    The endpoints of a selected link in the grid page are highlighted.  
  
2. In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, provide a (new) name for the link using the **Label** property.  
  
### To delete a link  
  
1.  In BizTalk Mapper, in a grid page, click a link to select it.  
  
     The endpoints of a selected link in the grid page are highlighted.  
  
2.  On the **Edit** menu, click **Delete**.  
  
     You can also press the DELETE key or right-click the link and click **Delete** on the shortcut menu.  
  
    > [!NOTE]
    >  You can bulk-select multiple link(s) and/or functoid(s) and then delete them in one operation. You can undo or redo the bulk deletion of link(s) and/or functoid(s). For more information about undo and redo operations, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).  
  
## See Also  
 [Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md)