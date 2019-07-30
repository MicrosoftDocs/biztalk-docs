---
title: "Settings to Check for All Connection Types2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e3f00ed-2660-4642-8eae-be3d5a04aa4a
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Settings to Check for All Connection Types
When you are configuring a new [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] connection or troubleshooting an existing connection, regardless of the connection type, the identifiers must match between the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] computer and the host. The type of identifier (ID or name) is as follows:  
  
 **For most mainframe connections**  
  
 **Node ID** is the identifier used when exchanging identification (XIDs) with most mainframes. Check to make sure that the following items match; if they do not, the Host Integration Server computer is not identifying itself in a way that the host can recognize.  
  
|Identifier used on mainframe|Identifier to configure on Host Integration Server|  
|----------------------------------|--------------------------------------------------------|  
|**IDBLK** and **IDNUM** in the PU definition|Two parts of the **Local Node ID** (configured on the connection)|  
  
 **For other mainframe connections**  
  
 There are some situations in which the mainframe does not use Node ID in XIDs, but instead uses Network Name and Control Point Name. These situations include mainframes communicating through LU 6.2, and mainframes that call up the Host Integration Server computer (meaning that the Host Integration Server computer accepts incoming calls on that mainframe connection). In these situations, the following parameters must match.  
  
> [!NOTE]
>  Change the following identifiers only when necessary. The local Network Name and the local Control Point Name should be changed only when the host requires a specific Network Name and Control Point Name that differ from those configured in the server properties.  
  
|Identifier used on mainframe (in unusual cases only)|Identifier to configure on Host Integration Server|  
|------------------------------------------------------------|--------------------------------------------------------|  
|**NETID** in the VTAM Start command for the local SSCP<br /><br /> **CPNAME** in the PU definition**NETID** and **SSCPNAME** in the VTAM Start command for the remote SSCP (VTAM system)|**Local Network Name** (configured on the server)<br /><br /> **Local Control Point Name** (configured on the server)<br /><br /> **Remote Network Name** and **Remote Control Point Name** (configured on the connection)|  
  
 **For AS/400 connections**  
  
 Network Name and Control Point Name (used together and called the fully qualified name) are the identifiers used when exchanging identification (XIDs) with AS/400 computers. Check to make sure that the following items match. If they do not, the Host Integration Server is not identifying itself in a way that the AS/400 can recognize.  
  
> [!NOTE]
>  Change the following identifiers only when necessary. To support multiple connections to the same AS/400, you must provide a unique local Network Name and local Control Point Name for each connection. In addition, you can change the local Network Name and the local Control Point Name if the host requires a specific Network Name and Control Point Name that differ from those configured in the server properties.  
  
|Identifier used on AS/400|Identifier to configure on Host Integration Server|  
|--------------------------------|--------------------------------------------------------|  
|**RMTNETID** (usually; often set to APPN); **RMTCPNAME**|**Local Network Name** and **Local Control Point Name** (configured on the server)|  
|**RMTNETID** (often set to APPN); **CP Name** (shown in the "Display network attributes" screen)|**Remote Network Name** and **Remote Control Point Name** (configured on the connection)|