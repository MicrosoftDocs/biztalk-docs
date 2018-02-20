---
title: "General Tab (Local Environment Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15329"
ms.assetid: dbbae0c5-dcdc-4aaf-930a-f64cc12e822c
caps.latest.revision: 3
robots: noindex,nofollow
---
# General Tab (Local Environment Properties)
Use the **General** tab to set the general local environment properties, including its name and basic information about its network type.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Local environment**|Type the name for the local environment. The name can be a maximum of 259 Unicode characters (alphabetic, numeric, space, and special). The name cannot be the same as that of an existing local environment. You can change the name at any time, unless the local environment is an associated listener in an application that is active. The application must be stopped before the LE can be renamed. After the name is changed, the new name will appear in the **Application**, **Local Environments** and **Object** nodes.|  
|**Network type**|Select the type of network used to communicate with the host. The choices are:<br /><br /> -   TCP/IP (default)<br />-   SNA. **Note:**  If the local environment is associated with any other configuration entity, you will receive an error when you attempt to apply the change.|  
|**Transport class**|Select the class of the transport object. This list changes according to the selected **Network type**.|  
|**Endpoint manager**|Select or type the local LU alias to manage the endpoint. **Note:**  The **Endpoint manager** edit box is set to **Localhost** and disabled if the **Network type** is set to **TCP/IP**.|  
|**Comment**|Type any additional information about the local environment. The comment can be a maximum of 259 Unicode characters (alphabetic, numeric, space, and special).|  
  
> [!CAUTION]
>  The properties of a local environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the local environment to function incorrectly.  
  
## See Also  
 [Local Environments Node](../core/local-environments-node1.md)   
 [Local Environment Node](../core/local-environment-node2.md)   
 [TI Manager Properties](../core/ti-manager-properties2.md)