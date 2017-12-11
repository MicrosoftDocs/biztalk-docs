---
title: "CICS Tab (for TCP-IP Properties)1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "15221"
ms.assetid: ae9e9791-3edc-4f7a-a4a1-17125d64509e
caps.latest.revision: 4
---
# CICS Tab (for TCP/IP Properties)
Use the **CICS** tab to set host-specific CICS properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Use IBM supplied CICS TCP/IP exit routine**|When security is enabled, the default TCP/IP header contains the userid followed by the password. Selecting **Use IBM supplied CICS TCP/IP exit routine**,however, overrides the default behavior and causes the TCP/IP header to put the password before the userid.|  
  
> [!CAUTION]
>  The properties of a remote environment are not intended to be set or changed programmatically. Setting or changing the properties programmatically might cause the remote environment to function incorrectly.  
  
## See Also  
 [TCP/IP Tab (Remote Environment Properties)](../HIS2010/tcp-ip-tab-remote-environment-properties-1.md)   
 [TI Manager Properties](../HIS2010/ti-manager-properties1.md)