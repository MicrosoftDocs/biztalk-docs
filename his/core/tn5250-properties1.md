---
title: "TN5250 Properties1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_TN5250Service"
ms.assetid: bbf4f548-eaf2-4107-99b3-e5cfbd5d88ef
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# TN5250 Properties
**Name**  
 Displays the name of the server running the TN5250 service. This field cannot be edited here.  
  
 **Comment**  
 Optionally, type a comment of up to 25 characters.  
  
 **Use Default**  
 Select **Use Default** to use the port number associated with telnet (as set in \\\DRIVERS\ETC\SERVICES).  
  
 **Use**  
 You can override the default value for a given server by selecting **Use** and typing another port number. You can also override this port number for a given session. TN services listen on multiple ports simultaneously. You can set a default port number for the TN service (assign the port number to the server) and override this number on a per session basis (assign the port number to the LU session), allowing a single client computer to connect to multiple host computers.  
  
## Host Integration Server, VTAM, and NCP Parameters for X.25 Connections  
 The following table shows how [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters for X.25 connections correspond to VTAM or NCP parameters. Asterisks (*) indicate required parameters.  
  
|Properties Tab|SNA Parameter|VTAM or NCP Parameter|  
|--------------------|-------------------|---------------------------|  
|System Identification|**Local Node ID**,* first three digits (block number)|**IDBLK=** parameter in the PU definition|  
|System Identification|**Local Node ID**,* last five digits (node number)|**IDNUM=** parameter in the PU definition|  
|System Identification|**Network Name (Remote Node)** Note: Network Name for local and remote nodes is generally the same|**NETID=** parameter in the VTAM Start command for the remote SSCP (VTAM system)|  
|System Identification|**Control Point Name (Remote Node)**|**SSCPNAME=** parameter in the VTAM Start command for the remote SSCP (VTAM system)|  
|Address|**Virtual Circuit Type or Remote X.25 Address**|**DIALNO=** parameter in the PORT definition|  
|X.25|**Max BTU Length**|**MAXDATA=** parameter in the PU definition (set Max BTU Length less than or equal to MAXDATA)|  
  
- Required parameter in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)].  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)