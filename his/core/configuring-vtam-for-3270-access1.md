---
title: "Configuring VTAM for 3270 Access1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a349060-e876-4be7-9db4-a78ea6a2d737
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Configuring VTAM for 3270 Access
When setting certain [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters for a host connection, you must match values set on the host or on front-end processors for the host. Host values are configured in VTAM. Front-end processor values are configured in the Network Control Program (NCP).  
  
 The following table shows how parameters for Host Integration Server correspond to VTAM host parameters.  
  
|Host Integration Server parameter|VTAM parameter|  
|---------------------------------------|--------------------|  
|**Control Point Name (Local Node)**.|**CPNAME=** in the PU definition.|  
|**Network Name (Local Node)** Note that the Network Name for the local and remote nodes is generally the same.|**NETID** parameter in the VTAM Start command for the local SSCP (the VTAM system to which Host Integration Server is attached). Note that this is generally the same as the NETID for the remote SSCP.|  
  
> [!NOTE]
>  The local Control Point Name and Network Name are needed only if the Host Integration Server will accept incoming calls, or will be used for LU6.2 (APPC).  
  
## See Also  
 [Host Configuration](../core/host-configuration1.md)