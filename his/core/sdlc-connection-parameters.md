---
title: "SDLC Connection Parameters2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18b7de30-6617-46ce-9a87-fcd9142171f9
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# SDLC Connection Parameters
The following table shows how [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] parameters for Synchronous Data Link Control (SDLC) connections correspond to VTAM or Network Control Program (NCP) parameters. Asterisks (*) indicate required parameters.  
  
|Host Integration Server parameter|VTAM or NCP parameter|  
|---------------------------------------|---------------------------|  
|**Local Node ID**,* first three digits (block number).|**IDBLK=** parameter in the PU definition|  
|**Local Node ID**,* last five digits (node number).|**IDNUM=** parameter in the PU definition|  
|**Network Name (Remote Node)** Note that the Network Name for the local and remote nodes is generally the same.|**NETID** parameter in the VTAM Start command for the remote SSCP (VTAM system)|  
|**Control Point Name (Remote Node)**.|**SSCPNAME** parameter in the VTAM Start command for the remote SSCP (VTAM system)|  
|**Max BTU Length**.|**MAXDATA=** parameter in the PU definition (set Max BTU Length ≤ MAXDATA)|  
|**Encoding** (NRZ or NRZI).|**NRZI=** setting in the LINE/GROUP definition (defaults to YES on host)|  
|**Local Poll Address**.|**ADDR**= parameter in the PU definition|  
  
 \* Required parameter in [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)]  
  
## See Also  
 [Host Configuration](../core/host-configuration.md)