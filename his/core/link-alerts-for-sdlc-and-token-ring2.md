---
title: "Link Alerts for SDLC and Token Ring2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f49395d-690f-4bdf-8e92-49276b258c3a
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Link Alerts for SDLC and Token Ring
When a Synchronous Data Link Control (SDLC) or Token Ring connection fails, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] logs diagnostic information, called link alerts, about the connection failure. The alerts are logged in a log file that can be viewed using the Windows Event Log service. To find a Host Integration Server log, in the Event Log service, on the Log menu, make sure Application is selected. Under the "Source" heading, the application log file will have a name starting with "SNA."  
  
 The link alerts are also used to build a network management vector transport (NMVT) alert, which includes probable causes and suggested actions for the alert. If a connection on the server running Host Integration Server has been designated for NetView, and the connection is active, the NMVT alert will be sent on that connection.  
  
 This section includes information that includes an explanation of the general format of link alerts, common to both SDLC and Token Ring, descriptions of individual alerts produced by the SDLC link service, detailed information about the local logging of SDLC alerts, descriptions of individual alerts produced by the Token Ring link service, and details of the local logging of Token Ring alerts.  
  
## In This Section  
 [Link Alert Format and Common Subvectors](../core/link-alert-format-and-common-subvectors2.md)  
  
 [SDLC Failure Alerts](../core/sdlc-failure-alerts2.md)  
  
 [SDLC Alert Local Logging](../core/sdlc-alert-local-logging1.md)  
  
 [Token Ring Failure Alerts](../core/token-ring-failure-alerts1.md)  
  
 For information about the NetView vectors supported by the NVAlert service, see [Alerts Used by Applications and NVAlert](../core/alerts-used-by-applications-and-nvalert2.md).  
  
## See Also  
 [Network Management with NetView](../core/network-management-with-netview1.md)