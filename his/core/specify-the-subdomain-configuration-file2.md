---
title: "Specify the Subdomain Configuration File2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88a2ffa4-b4cd-4311-a4a1-ba9710a41c89
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Specify the Subdomain Configuration File
Within a [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] command (a **snacfg** command), you can specify the path of the subdomain configuration file to access, or you can omit the path. If you omit the path, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] attempts to access the configuration file in the normal location on the local system: <em>\\</em>Program Files\Host Integration Server\SYSTEM\CONFIG\COM.CFG. To specify the path of the configuration file to access, type the **snacfg** command with the following syntax:  
  
```  
  
configpath command options  
  
```  
  
 That is, follow the **snacfg** command with a space, a pound sign, then the configuration path, and then any additional command syntax.  
  
 For example, to view a listing of the connections stored in Program Files\Host Integration Server\SYSTEM\CONFIG\BACKUP.SNA, type  
  
## See Also  
 [Snacfg Reference](../core/snacfg-reference2.md)