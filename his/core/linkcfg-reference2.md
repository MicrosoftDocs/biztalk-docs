---
description: "Learn more about: Linkcfg Reference"
title: "Linkcfg Reference2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Linkcfg Reference
Allows you to install and delete link services from the command prompt. Linkcfg allows you to build script files to add link services. If you need to uninstall or reinstall [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], you can reinstall link services by running the Linkcfg script files.  
  
 To view the list of link services you can install using Linkcfg, type the command linkcfg. The following appears:  
  
```  
LINKCFG [ LINKSVC /LSTYPE:{
"Distributed Link Service"           |
"DEMO SDLC Link Service"             |
"IP-DLC Link Service"  } ]
[ @commandfile ]  
  
```  
  
> [!NOTE]
>  If one of the link services was not copied during Setup, it will not appear on the list.  
  
 When setting the parameters for each of the link services, you must type the link service exactly as it appears above.  
  
 The configurable parameters for each link service are provided in the command-line help. To see the parameters for each, type the following:  
  
 LINKCFG LINKSVC /LSTYPE:"name of link service" where the name is one of those listed above. The available parameters will appear on the screen.  
  
 The following sections reference specific areas of Linkcfg.  
  
 This section contains:  
  
-   [Linkcfg Error Messages](../core/linkcfg-error-messages1.md)  
  
-   [Demo SDLC Link Service](../core/demo-sdlc-link-service-linkcfg-1.md)  
  
-   [Distributed Link Service](../core/distributed-link-service1.md)  
  
## See Also  
 [Command-Line Interface](../core/command-line-interface2.md)
