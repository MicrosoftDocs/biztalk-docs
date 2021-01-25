---
description: "Learn more about: How to Optimize the Schema Tree View"
title: "How to Optimize the Schema Tree View | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab4ad6b5-5bbd-443b-9041-6cddf9d64735
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Optimize the Schema Tree View
You can use the **Relevance View** in BizTalk Mapper to optimize the source and/or target schema trees. This topic provides instructions about how to perform the operation.  
  
 The relevance view uses sibling coalescence to collapse the non-relevant schema elements to provide a more compact view of the schema. This further reduces the need of scrolling and helps you focus on your requirement for using schemas and maps.  
  
 The following figure shows a schema when the relevance view is turned OFF. The schema pane displays all nodes, irrespective of whether the nodes are part of any relationship or not.  
  
 ![Schema when relevance view is switched off](../core/media/off-schema-relevance-view.gif "Off_Schema_Relevance_View")  
  
 Click the ![Switch to relevance view](../core/media/mapper-intellitree.gif "Mapper_IntelliTree") icon on the Mapper utility ribbon to turn the relevance view ON. You can switch to relevance view for any one or both the source schema and the target schema; click the respective icons for source and target schemas.  
  
 When you switch to relevance view for a schema:  
  
-   All the record elements that do not have any links either for them or their child field elements are collapsed.  
  
-   All successive nodes that do not have any links are coalesced and are replaced by the ![Coalesced nodes hidden](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icon. The BizTalk Mapper looks for a minimum of two successive non-relevant nodes that can be coalesced. You can move the mouse over the icon to view the list of coalesced nodes. Note that the infotip will only list the names of the first three coalesced nodes, even if there are more coalesced nodes. You can view all the nodes by clicking the ![Coalesced nodes hidden](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icon.  
  
    > [!NOTE]
    >  For more information about infotip, see [How to View Infotip and Tooltip](../core/how-to-view-infotip-and-tooltip.md).  
  
## Prerequisites  
 This operation requires that BizTalk Mapper is running.  
  
## To optimize the schema tree view  
 On the Mapper utility ribbon, turn ON the relevance view for source and/or target schemas by clicking the respective ![Switch to relevance view](../core/media/mapper-intellitree.gif "Mapper_IntelliTree") icons. The following figure shows the same schema when the relevance view is turned ON. All the non-relevant nodes are replaced by the ![Coalesced nodes hidden](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icon to provide a more compact view of the schema.  
  
 ![Schema when relevance view is ON](../core/media/on-schema.gif "On_schema")  
  
 When you expand the coalesced nodes in source and/or destination schemas, the ![Coalesced nodes hidden](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") changes to ![Coalesced nodes shown](../core/media/switchoff-mapper-coalesence.jpg "SwitchOff_Mapper_Coalesence") icon.  
  
> [!NOTE]
>  You can press CTRL+M, CTRL+E or CTRL+M, CTRL+C to expand or collapse the tree nodes in source schema respectively. Similarly, you can press CTRL+M, CTRL+E or CTRL+M, CTRL+C to expand or collapse the tree nodes in destination schema respectively. You can also press Ctrl+M, Ctrl+H or Ctrl+M, Ctrl+D for source or target coalescing respectively. For a list of Mapper keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
## See Also  
 [Using Enhanced Features in BizTalk Mapper](../core/using-enhanced-features-in-biztalk-mapper.md)
