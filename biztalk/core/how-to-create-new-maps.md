---
title: "How to Create New Maps | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43b36cd8-f28e-4349-87d5-c94b7d8761bf
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create New Maps

## Overview
To build a new BizTalk map, there are three high-level steps to perform:  
  
1. Create the new map within a BizTalk project.  
  
2. Add the source and destination schemas to the map.  
  
3. Build the set of links and, perhaps, intermediate functoids specifying how the source schema maps to the destination schema.  
  
   In the current context, the first two of these three steps is considered "creating" the map. The third step is considered "building" the map. For step-by-step instructions on many of the tasks related to the process of building the map, see [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md).  
  
## Create a new map 
  
1. Right-click a BizTalk project in Solution Explorer, select **Add**, and then select **New Item**.  
  
2. In the **Add New Item** dialog box, in the **Templates** area, select **Map**.  
  
3. Select the text in the **Name** box, type a name for the map, and then select **Add**.  
  
    BizTalk Mapper opens in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window, showing three distinct panes, side-by-side. From left to right, these panes show the source schema, the grid (which may have multiple pages), and the destination schema.  
  
   > [!IMPORTANT]
   >  You cannot use the following names for maps: "XmlContent", "SourceSchemas", "TargetSchemas", or "XsltArgumentListContent". These names cannot be used because compilation into a .NET assembly produces naming restrictions as the result of generated C# code.  
  
4. In BizTalk Mapper, in the left pane, select **Open Source Schema**.  
  
5. In the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the appropriate source schema, and then select **OK**.  

   > [!TIP]
   > **Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can resize the Type Picker window to see the full name of your schema.
  
    If only a single root exists in the source schema, or a root node has been established for the schema using the **Root Reference** property of the **Schema** node, the source schema opens in the left pane, and you can proceed to step 7.  
  
6. If the source schema has multiple root nodes, and no root node has been established for the source schema using the **Schema** node's **Root Reference** property, in the **Root Node for Source Schema** dialog box, select the appropriate root node, and select **OK**.  
  
   > [!IMPORTANT]
   >  If you choose a root node for a schema in BizTalk Mapper and then later change the **Root Reference** property in the schema, the next time you open the schema in BizTalk Mapper, the root node will not update to the new root reference configured in BizTalk Editor.  
  
7. In BizTalk Mapper, in the right pane, select **Open Destination Schema**.  
  
8. In the **BizTalk Type Picker** dialog box, expand the **Schema** node in the tree, if necessary, select the appropriate destination schema, and then select **OK**.  
  
    If only a single root exists in the destination schema, or a root node has been established for the destination schema using the **Root Reference** property of the **Schema** node, the destination schema opens in the right pane, and you will not need to perform step 9.  
  
9. If the destination schema has multiple root nodes, and no root node has been established for the destination schema using the **Root Reference** property of the **Schema** node, in the **Root Node for Target Schema** dialog box, select the appropriate root node, and select **OK**.  
  
     The destination schema opens in the right pane.  
  
## See Also  
 [Managing Maps Within Projects](../core/managing-maps-within-projects.md)