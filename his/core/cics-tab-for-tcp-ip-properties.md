---
title: "CICS Tab (for TCP-IP Properties)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15221"
ms.assetid: 99231fab-087e-40bd-9b52-1044462e6951
caps.latest.revision: 3
robots: noindex,nofollow
---
# CICS Tab (for TCP/IP Properties)
Use the **CICS** tab to set host-specific CICS properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use IBM supplied CICS TCP/IP exit routine**|When security is enabled, the default TCP/IP header contains the userid followed by the password. Selecting **Use IBM supplied CICS TCP/IP exit routine**,however, overrides the default behavior and causes the TCP/IP header to put the password before the userid.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [TCP/IP Tab (Remote Environment Properties)](../core/tcp-ip-tab-remote-environment-properties.md)   
 [TI Manager Properties](../core/ti-manager-properties.md)