---
title: "General Tab (View Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15336"
ms.assetid: a6da9ade-533d-433d-a0e9-7d995c41cf35
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
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
 [View Node (listener)](../core/view-node-listener.md)   
 [View Node (object)](../core/view-node-object.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)