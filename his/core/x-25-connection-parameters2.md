---
description: "Learn more about: X.25 Connection Parameters"
title: "X.25 Connection Parameters2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# X.25 Connection Parameters
The following table shows how [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] parameters for X.25 connections correspond to VTAM or Network Control Program (NCP) parameters. Asterisks (*) indicate required parameters.  
  
|Host Integration Server parameter|VTAM or NCP parameter|  
|---------------------------------------|---------------------------|  
|**Local Node ID**,* first three digits (block number).|**IDBLK=** parameter in the PU definition|  
|**Local Node ID**,* last five digits (node number).|**IDNUM=** parameter in the PU definition|  
|**Network Name (Remote Node)** Note that the Network Name for the local and remote nodes is generally the same.|**NETID** parameter in the VTAM Start command for the remote SSCP (VTAM system)|  
|**Control Point Name (Remote Node)**.|**SSCPNAME** parameter in the VTAM Start command for the remote SSCP (VTAM system)|  
|**Remote X.25 Address***.|**DIALNO=** parameter in the PORT definition|  
|**Max BTU Length**.|**MAXDATA=** parameter in the PU definition (set Max BTU Length ≤ MAXDATA)|  
  
 \* Required parameter in [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)]  
  
## See Also  
 [Host Configuration](../core/host-configuration1.md)
