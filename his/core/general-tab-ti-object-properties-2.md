---
title: "General Tab (TI Object Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54348bbd-a985-4f3f-84d3-58f01354927f
caps.latest.revision: 3
robots: noindex,nofollow
---
# General Tab (TI Object Properties)
Use the **General** tab to define the basic characteristics of the object that will service requests from the Windows platform.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Object**|View the ProgID that names the component. This ProgID is created by Visual Studio in Host Integration Server (Designer in SNA Server) using the type library name, the interface name, and the version information given for the component.|  
|**Type**|View the type of remote environment for which this component is designed. This type is specified in Visual Studio when the component's type library is created. **Note:**  You cannot change the type of an object.|  
|**Description**|View the component description entered in Visual Studio when the component's type library was created.|  
|**File**|View the name of the component library.|  
|**CLSID**|View the CLSID that uniquely identifies the component.|  
|**Comment**|Type a comment that provides additional information about the use of the object. The comment can be a maximum of 259 Unicode characters.|  
  
> [!CAUTION]
>  The properties on an object are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the object to function incorrectly.  
  
## See Also  
 [Objects Node (WIP)](../core/objects-node-wip-1.md)   
 [Object Node (WIP)](../core/object-node-wip-1.md)   
 [TI Manager Properties](../core/ti-manager-properties2.md)