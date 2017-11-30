---
title: "General Tab (View Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15336"
ms.assetid: 9f68fbdc-8a09-42a6-a256-212e1fbff8fc
caps.latest.revision: 4
---
# General Tab (View Properties)
Use the **General** tab to view or change the basic information about the object view.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Object view**|View the name of the object view.|  
|**Local environment**|Select a local environment (LE). The LE determines the network type associated with the object view.<br /><br /> If you are changing from one network type to another, be sure to remove all methods from the view before changing the LE. **Note:**  Changing the current LE in the view removes the host environments (HEs) associated with the view and all related information. Use the **Host Environments** tab to associate a new HE.|  
|**Security policy**|Select a security policy to be associated with the view.|  
|**Comment**|Type a comment that provides additional information about the use of the object view in the HIP environment. The comment can be a maximum of 259 alpha-numeric characters.|  
  
> [!NOTE]
>  When viewed from the ***view*** node under the application ***listener*** node, the general properties are read-only. If you want to change a general property, right-click the specific ***view* Node** under the ***object* Node**, and then left-click **Properties** on the shortcut menu. The properties on that page are read-write.  
  
> [!CAUTION]
>  The properties on an object view are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the application to function incorrectly.  
  
## See Also  
 [View Node (listener)](../HIS2010/view-node-listener-1.md)   
 [View Node (object)](../HIS2010/view-node-object-2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)