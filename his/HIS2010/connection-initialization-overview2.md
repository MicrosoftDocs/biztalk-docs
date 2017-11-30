---
title: "Connection Initialization Overview2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66466145-9220-4ce3-a46d-40b963160bfc
caps.latest.revision: 4
---
# Connection Initialization Overview
Connection Initialization occurs in a sequential fashion. Each step builds upon the preceding step. After all steps have completed correctly, an Active connection is established between [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] and a remote host, either an AS/400 or a mainframe.  
  
 Every connection requires that a number of parameters match between the two platforms. Throughout this overview, these parameters, indicated in bold type, are displayed using the actual field names used by Host Integration Server and a remote host (that is, upper/lower case is preserved).  
  
## Steps 1 and 2  
 Verify basic network connectivity - can Host Integration Server communicate with the host's network adapter card?  
  
 Does the **Remote Network Address** on the **Address** tab of the **Connection Properties** dialog box match the **Local Adapter Address** defined in the AS/400 line description, or the **Switched Line** in the VTAM definition?  
  
## Steps 3 and 4  
 Verify host SSAP - is the host listening on the correct Source Service Access Port?  
  
 Does the **Remote SAP Address** on the **Address** tab of the **Connection Properties** dialog box match the **LAN SSAP** defined in the APPC Controller Description, or the **Switched Line** in the VTAM definition?  
  
## Steps 5 and 6  
 Verify local parameters - do the Host Integration Server "Local" parameters on the **System** tab of the **Connection Properties** dialog box match the "Remote" parameters in the host APPC controller, or VTAM PU, definition?  
  
## Step 7  
 Verify remote parameters - do the Host Integration Server "Remote" parameters, also defined on the **System** tab of the **Connection Properties** dialog box, match the "Local" parameters in the host APPC controller, or VTAM PU definition?  
  
 Connection initialization is a complex, sequential process that includes a wealth of details.  
  
 For more information, see [Connection Initialization Details](../HIS2010/connection-initialization-details1.md).