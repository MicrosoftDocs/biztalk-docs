---
title: "Locale Tab (Remote Environment Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15218"
ms.assetid: b5d435e3-3cd6-4780-904f-4aaca46d4617
caps.latest.revision: 4
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
 [Remote Environments Node](../HIS2010/remote-environments-node1.md)   
 [Remote Environment Node](../HIS2010/remote-environment-node2.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)