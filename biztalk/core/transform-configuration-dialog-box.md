---
title: "Transform Configuration Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.transform.config"
ms.assetid: 7956489d-94ac-4e7d-b3a2-4a2fc059fd3c
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transform Configuration Dialog Box
You use the **Transform Configuration** dialog box to configure the Transform shape. You assign a map to the Transform shape, either by creating a new one or by selecting an existing one, and you define source and destination messages to use in the transform.  
  
|Use this|To do this|  
|--------------|----------------|  
|**New Map**|Create a new map to do the transformation.|  
|**Existing Map**|Use an existing map to do the transformation.|  
|**Fully Qualified Map Name**|Type a name for a new map, or use the drop-down list to select an existing map.|  
|**Source**|From the grid, select a source message for the transform. **Note:**  Valid messages may be marked as invalid (red cross); this most often occurs when the message schema and map are in different projects. If your message is valid, you can safely ignore the invalid message icon.|  
|**Destination**|From the grid, select a destination message for the transform. **Note:**  Valid messages may be marked as invalid (red cross); this most often occurs when the message schema and map are in different projects. If your message is valid, you can safely ignore the invalid message icon.|  
|**When I click OK, launch the BizTalk Mapper**|Invoke the mapper to create or edit a map to use in the transform.|  
  
## See Also  
 [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md)