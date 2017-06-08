---
title: "BizTalk Mapper Grid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.mapper.grid"
helpviewer_keywords: 
  - "BizTalk Mapper, mapping records"
  - "mapping, records"
  - "mapping, fields"
  - "BizTalk Mapper, map grid"
  - "fields, mapping"
  - "BizTalk Mapper, mapping fields"
  - "functoids, mapping"
  - "mapping, functiods"
ms.assetid: 3ac092c0-a58b-4b8b-ac06-b7d8e729a489
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Mapper Grid
Use the grid within BizTalk Mapper to define how records and fields in your source schema map to records and fields in your destination schema.  
  
 If you drag a record or field in the source or destination schema directly to a record or field in the other schema, the link connecting these fields will be routed through the BizTalk Mapper grid.  
  
 If a particular mapping requires the use of one or more functoids, first drag and drop the appropriate functoid(s) from the appropriate functoid category tab in the Microsoft Visual Studio toolbox to the BizTalk Mapper grid. Then create the links between the functoid(s) and the appropriate records or fields in the source and destination schema by dragging the functoid, record, or field to the functoid, record, or field with which you want it to be linked. Links can be created in either direction.  
  
|Use this|To do this|  
|--------------|----------------|  
|Large white arrows that appear when you put the cursor near an edge or corner of the grid.<br /><br /> Examples:<br /><br /> **Grid scrolling arrow - northeast**<br /><br /> ![](../core/media/bts-gridgone.gif "bts_gridgone")<br /><br /> **Grid scrolling arrow - west**<br /><br /> ![](../core/media/bts-gridgowest.gif "bts_gridgowest")|Scroll the grid in the direction of the arrow to show a portion of the grid that was not previously viewable.|  
|Functoid category tabs in the Visual Studio toolbox.|Expose sets of related functoids that you can drag to the grid.|  
|**First grid page button**<br /><br /> ![](../core/media/bts-layerfirst.gif "bts_layerfirst")|Scrolls the page tab to view the first grid page.|  
|**Previous grid page button**<br /><br /> ![](../core/media/bts-layerleft.gif "bts_layerleft")|Scrolls the next grid page to the left of the currently visible grid page so you can view it.|  
|**Next grid page button**<br /><br /> ![](../core/media/bts-layerright.gif "bts_layerright")|Scrolls the next grid page to the right of the currently visible grid page so you can view it.|  
|**Last grid page button**<br /><br /> ![](../core/media/bts-layerlast.gif "bts_layerlast")|Scrolls the page tab to view the last grid page.|  
|Page **\<N>** tab(s)|Bring the corresponding grid page to the top, so you can view it.<br /><br /> Grid pages can be renamed; their default names are "Page 1," "Page 2," and so on.|  
|**Grid Preview** command on the shortcut menu associated with the grid area.|Open the **Grid Preview** dialog box so you can navigate more effectively when working with large grids (map grid pages).<br /><br /> This command is also available on the **BizTalk** menu.|  
|**Add Page** command on the shortcut menu associated with the page tabs.|Add a new grid page. New grid pages have a default name of the form "Page **N**", where "**N**" is a monotonically increasing number starting at "2."<br /><br /> This command is also available on the **BizTalk** menu.|  
|**Delete Page** command on the shortcut menu associated with the page tabs.|Delete the currently selected grid page. You will be prompted to confirm the deletion of the page and any links and functoids it contains.<br /><br /> This command is also available on the **BizTalk** menu.|  
|**Rename Page** command on the shortcut menu associated with the page tabs.|Rename the currently selected grid page.<br /><br /> This command is also available on the **BizTalk** menu.|  
|**Reorder Pages** command on the shortcut menu associated with the page tabs.|Open the **Reorder Pages** dialog box within which the order of grid pages can be rearranged.<br /><br /> This command is also available on the **BizTalk** menu. **Note:**  This command is not available unless there is more than one grid page.|  
  
## See Also  
 [Grid Properties](../core/grid-properties.md)