---
title: "Endpoints Tab (SNA Listener Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15325"
ms.assetid: aebec5e0-9560-419e-9798-6b1f9ef66f2c
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
robots: noindex,nofollow
---
# Endpoints Tab (SNA Listener Properties)
The **Endpoints** tab displays the defined endpoints in the local environment definition. The controls on the **Endpoints** tab are read-only. To add or remove endpoints from the local environment, use the **Properties** shortcut menu item on the **Local Environments** node.  
  
|Use this|To do this|  
|--------------|----------------|  
|**New transaction program name**|View the transaction program (TP) name or the link mirror transaction ID of the local environment.|  
|**Add**|Not available.|  
|**Defined transaction programs names**|View the existing TP names or the link mirror transaction IDs for the local environment.|  
|**Remove**|Not available.|  
  
> [!NOTE]
>  When viewed from the ***listener*** node, the endpoint properties are read-only. If you want to change an endpoint property, right-click the specific ***local environment* Node** under the **Local Environments Node**, and then left-click **Properties** on the shortcut menu. The properties on that page are read-write.  
  
> [!CAUTION]
>  The properties of an listenerare not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the application to function incorrectly.  
  
## See Also  
 [Listener](../core/listener.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)