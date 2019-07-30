---
title: "Mainframe Connections without XIDs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 660d6ea4-2ce6-458a-9c09-289bf592e87a
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Mainframe Connections without XIDs
There are some situations in which the mainframe does not use Node ID in exchange identifications (XIDs), but instead uses Network Name and Control Point Name. These situations include mainframes communicating through LU 6.2 and mainframes that call up [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]. (Host Integration Server accepts incoming calls on that mainframe connection.) In these situations, the following parameters must match.  
  
> [!NOTE]
>  Use the following identifiers only when necessary. They are more complicated than needed for most mainframe connections and add the potential for error when used unnecessarily.  
  
|Identifier used on mainframe<br /><br /> (in unusual cases only)|Identifier to configure<br /><br /> on Host Integration Server|  
|----------------------------------------------------------------|------------------------------------------------------------|  
|**NETID** in the VTAM Start command for the local SSCP<br /><br /> **CPNAME** in the PU definition<br /><br /> **NETID** and **SSCPNAME** in the VTAM Start command for the remote SSCP (VTAM system)|**Local Network Name** (configured on the server)<br /><br /> **Local Control Point Name** (configured on the server)<br /><br /> **Remote Network Name** and **Remote Control Point Name** (configured on the connection)|  
  
## See Also  
 [Host Configuration](../core/host-configuration1.md)