---
title: "Format for Alerts Used by Applications and NVAlert1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f91a82ba-d83b-40df-958d-910bddc0c24d
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Format for Alerts Used by Applications and NVAlert
An application program or the NVAlert service can use the CSV **TRANSFER_MS_DATA** to issue alerts. The alerts are logged in a log file that can be viewed using the Windows Event Log service, and may also be sent on the NetView connection.  
  
 The data supplied to **TRANSFER_MS_DATA** may be in any of the following formats:  
  
 NMVT  
 The application or service supplies a complete NMVT, including the header information.  
  
 ALERT_SUBVECTORS  
 The application or service supplies the subvectors required for an alert, but without the NMVT header or major vector header. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] adds the header information, as described in the next section.  
  
 PDSTATS_SUBVECTORS  
 The application or service supplies the subvectors required for a Problem Determination Statistics NMVT, but without the NMVT header or major vector header. [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] adds the header information, as described in the next section.  
  
 USER_DEFINED  
 The application or service supplies data in its own format. This data cannot be sent on the connection designated for NetView, but is logged in the same way as the other data formats.  
  
 The application or service can also request Host Integration Server to add the Product Set ID subvector (for all data types except USER_DEFINED), the Date/Time subvector, or both to the supplied data. The format of these added subvectors is described in the next section.  
  
 For all data types, the data (with added headers and subvectors, if appropriate) is logged locally in NMVT format, whether or not you specified a connection for NetView.  
  
## See Also  
 [Added Headers and Subvectors](../core/added-headers-and-subvectors1.md)