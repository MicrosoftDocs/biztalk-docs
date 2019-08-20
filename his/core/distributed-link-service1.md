---
title: "Distributed Link Service1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a30704f-65e6-4232-8040-931983136c16
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Distributed Link Service
Linkcfg options for distributed link service.  
  
> [!NOTE]
>  Configuration settings specified withlinkcfgcorrespond to local link configuration settings in the SNA Manager.  
  
## Syntax  
  
```  
LINKCFG LINKSVC "title"  
     /SERVER:servername  
     /LSTYPE:"Distributed Link Service"  
     /REMOTELINKTYPE:{ Channel | Ethernet802.2 | LeasedSDLC |   
                       SwitchedSDLC | TokenRing802.2 | Twinax | X.25QLLC }  
     /REMOTELIST:\\server\service[;\\server\service;...]  
     /ALTLIST:\\server\service[;\\server\service;...]  
     /DOMAIN:domain  
     /USERID:userid  
     /PASSWORD:password  
```  
  
 **/LINKSVC**" *title*"  
 Enter the name of the distributed link service. The quotes must be included. Any title name can be used.  
  
 **/SERVER:** *servername*  
 This is the name of the computer on which the link service is to be installed.  
  
 **/LSTYPE:**"Distributed Link Service"  
 This parameter is used to list the available options for the distributed link service. You must type in the exact string as shown above for it to work correctly. The quotes must be included.  
  
 **/REMOTELINKTYPE:{ Channel &#124; Ethernet 802.2 &#124; LeasedSDLC &#124; SwitchedSDLC &#124; TokenRing802.2 &#124; Twinax &#124; X.25 }**  
 This parameter defines the remote link type for the distributed link service.  
  
 **/REMOTELIST:**\\\ *server*\ *service*[;\\\ *server*\ *service*;]  
 This is the name of the remote link service, for example \\\SNASERV1\SNADLC1;\\\SNASERV2\SNADLC1.  
  
 **/ALTLIST:** \\\server\service[;\\\server\service;]  
 These are the names of alternate (backup) link services using the preceding format and example.  
  
 **/DOMAIN:** *domain*  
 Enter the name of the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] subdomain.  This is a required parameter if [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is installed on a system account, not a local account.  
  
 **/USERID:** *userid*  
 Enter the name of the userid for the system account.  This is a required parameter if [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is installed on a system account, not a local account.  
  
 **/PASSWORD:** *password*  
 Enter the password of the system account.  This is a required parameter if [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is installed on a system account, not a local account.  
  
## See Also  
 [Linkcfg Reference](../core/linkcfg-reference2.md)