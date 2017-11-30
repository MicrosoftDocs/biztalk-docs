---
title: "Host Environments Tab (View Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15338"
ms.assetid: a2486c30-2a06-4e6a-a8f1-5c03cb749c8e
caps.latest.revision: 4
---
# Host Environments Tab (View Properties)
Use the **Host Environments** tab to view or change detailed information about the host environments (HEs) associated with the object view.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Host environment**|Select the host environment to associate with the object view. This list includes all the HEs that have the same network type as the local environment associated with the object view.|  
|**Configured host environments**|View the HEs already associated with the object view.|  
|**Add**|Click to add the HE to the object view and move the name to **Configured host environments**.|  
|**Remove**|Click to remove the selected HE from the object view and from **Configured host environments**. The removed HE is moved to the list in **Host environment**.|  
  
> [!NOTE]
>  When viewed from the ***view*** node under the application ***listener*** node, the host environment properties are read-only. If you want to change a host environment property, right-click the specific ***view* Node** under the ***object* Node**, and then left-click **Properties** on the shortcut menu. The properties on that page are read-write.  
  
> [!CAUTION]
>  The properties on an object view are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the object view to function incorrectly.  
  
## See Also  
 [View Node (listener)](../HIS2010/view-node-listener-1.md)   
 [View Node (object)](../HIS2010/view-node-object-2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)