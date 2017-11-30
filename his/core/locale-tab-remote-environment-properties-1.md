---
title: "Locale Tab (Remote Environment Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15218"
ms.assetid: bb071ad4-92ab-4483-b9ba-5e3e92d446c6
caps.latest.revision: 3
robots: noindex,nofollow
---
# Locale Tab (Remote Environment Properties)
Use the **Locale** tab to define the computer data type characteristics used by the host that makes accepts requests from the Windows platform.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Locale**|Select the language locale you want to use in selecting the code page used by the TI run-time environment.|  
|**Use default code page for the selected locale**|Select this option to have TI select the default code page suitable for the specified locale. If you clear this check box, you must explicitly select the code page.|  
|**Code page**|Select the code page used to transform the incoming and outgoing data to a form that can be used by the host application program.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [Remote Environments Node](../core/remote-environments-node2.md)   
 [Remote Environment Node](../core/remote-environment-node1.md)   
 [TI Manager Properties](../core/ti-manager-properties2.md)