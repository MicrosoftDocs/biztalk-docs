---
title: "General Tab (Remote Environment Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15212"
ms.assetid: d6da4934-9f8d-45df-87ab-11ee2632c872
caps.latest.revision: 3
robots: noindex,nofollow
---
# General Tab (Remote Environment Properties)
Use the **General** tab to set the basic characteristics of the remote environment.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Type**|View the type of remote environment, which describes the region on the mainframe with which your application is designed to work|  
|**Status**|View the current state of the remote environment:<br /><br /> -   **Active**. The TI run-time environment accepts requests and attempts to communicate with the associated mainframe region.<br />-   **Inactive**. The TI run-time environment will not accept requests from client applications and returns an Inactive remote environment error message without attempting to communicate with the associated mainframe region.<br />-   **Disabled**.|  
|**Identifier**|View the GUID for the remote environment. This identifier is useful when reviewing TI messages in the Windows Event Log.|  
|**Creator name**|View the user ID of the user who created the remote environment.|  
|**Date created**|View the date the remote environment was created.|  
|**Comment**|Type or view a comment or description to help identify the new remote environment when its properties are displayed elsewhere in the product. You can enter up to 259 Unicode characters in this field. Useful information includes the name and location of the mainframe, and the name and telephone number of the system administrator.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [Remote Environments Node](../core/remote-environments-node2.md)   
 [Remote Environment Node](../core/remote-environment-node1.md)   
 [TI Manager Properties](../core/ti-manager-properties2.md)