---
title: "Configure &lt;Functoid&gt; Functoid Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.mapper.functoid.inputs"
helpviewer_keywords: 
  - "BizTalk Mapper, input parameters"
  - "funtoids, mapping"
  - "BizTalk Mapper, functoids"
  - "functoids, BizTalk Mapper"
ms.assetid: 1fd1d80f-c5c2-4ae7-8f29-c510c2927ef4
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure &lt;Functoid&gt; Functoid Dialog Box
Use the **Configure \<Functoid> Functoid** dialog box to manage the input parameters to the selected functoid. Input parameters from records and fields in the source schema and from other functoids are established by dragging between the relevant items to create links that connect to the left side of the functoid. This dialog box enables you to add constant input parameters, change the order of input parameters (regardless of how they were created), and delete incorrect input parameters.  
  
> [!NOTE]
>  If an input parameter to a functoid is not valid, a default value is passed to the functoid in its place. For numeric input parameters, the default value is zero (0). For all other input parameters, the default value is blank.  
  
## Input Parameters  
 Examine the existing ordered set of input parameters. Select an input parameter in this list to perform actions such as changing its position in the order or editing the constant value associated with the input parameter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Edit functoid constant**|Open the **Functoid Constant Value** dialog box to edit the value associated with a constant input parameter.<br /><br /> When you initially add a constant input parameter, or double-click an existing constant input parameter, you can edit its value in place.|  
|**Insert new constant**|Insert a new constant input parameter at the end of the list of input parameters.<br /><br /> Immediately after you click this button, you can begin editing the constant value.<br /><br /> After inserting a new constant input parameter, you can use the up and down arrow buttons to move it to the proper location within the ordered list of input parameters.|  
|**Delete selected input parameter**|Delete the selected input parameter from the ordered list of input parameters.|  
|**Move selected input parameter up**|Exchange the selected input parameter with the input parameter immediately above it in the ordered list, changing the order in which these parameters are passed to the corresponding functoid.|  
|**Move selected input parameter down**|Exchange the selected input parameter with the input parameter immediately below it in the ordered list, changing the order in which these parameters are passed to the corresponding functoid.|  
|**Parameter count statement**|Examine the parameter count requirements of the current functoid. This statement is located immediately below the **Input parameters** list.|  
|**Functoid description**|Read about the purpose and use of the functoid without needing to look at the online Help.|  
  
## See Also  
 [General Functoid Properties](../core/general-functoid-properties.md)   
 [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md)