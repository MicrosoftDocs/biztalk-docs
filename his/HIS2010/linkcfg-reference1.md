---
title: "Linkcfg Reference1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74bd92bd-54f3-47d7-8f41-a5ac140a2c9d
caps.latest.revision: 6
---
# Linkcfg Reference
Allows you to install and delete link services from the command prompt. Linkcfg allows you to build script files to add link services. If you need to uninstall or reinstall [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], you can reinstall link services by running the Linkcfg script files.  
  
 To view the list of link services you can install using Linkcfg, type the command linkcfg. The following appears:  
  
```  
LINKCFG [ LINKSVC /LSTYPE:{   
"Andrew Twinax Link Service"|  
"Atlantis/SAGEM SDLC Link Service"|  
"Atlantis/SAGEM X.25 Link Service"|  
"DCA ISCA SDLC Link Service"|  
"DCA ISCA X.25 Link Service"|  
"DEMO SDLC Link Service"  
"Distributed Link Service"|  
"DLC 802.2 Link Service"|  
"IBM SDLC Link Service"|  
"IBM Twinax Link Service"|  
"IBM X.25 Link Service"|  
"MicroGate SDLC Link Service"|  
"MicroGate X.25 Link Service" } ]  
 [ @commandfile ]  
  
```  
  
> [!NOTE]
>  If one of the link services was not copied during Setup, it will not appear on the list.  
  
 When setting the parameters for each of the link services, you must type the link service exactly as it appears above.  
  
 The configurable parameters for each link service are provided in the command-line help. To see the parameters for each, type the following:  
  
 LINKCFG LINKSVC /LSTYPE:"name of link service" where the name is one of those listed above. The available parameters will appear on the screen.  
  
 The following sections reference specific areas of Linkcfg.  
  
 This section contains:  
  
-   [Linkcfg Error Messages](../HIS2010/linkcfg-error-messages2.md)  
  
-   [Demo SDLC Link Service](../HIS2010/demo-sdlc-link-service-linkcfg-2.md)  
  
-   [Distributed Link Service](../HIS2010/distributed-link-service2.md)  
  
## See Also  
 [Command-Line Interface](../HIS2010/command-line-interface1.md)