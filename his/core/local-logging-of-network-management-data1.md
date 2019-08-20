---
title: "Local Logging of Network Management Data1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6736b9b-2d9d-4a16-9326-605938cff374
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Local Logging of Network Management Data
Data is logged in a Windows Event Log service log file in two ways. First, the data from the alert is logged in a more readable format, using standard log messages. The format is specific to the alert type. For the message numbers used and explanations of the data, see the section in this documentation that relates specifically to that type of alert.  
  
 If a connection has been designated for carrying NetView data and the server that owns the connection is active, the alert NMVT containing the data is also logged in NMVT format as it would be sent. The NMVT appears as Message 540, followed by Message 541. Note that this logging occurs before [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] attempts to send the NMVT. The log is therefore no guarantee that the NMVT is sent successfully.  
  
 For more information about local logging of alert information, see the section in this documentation relating specifically to that type of alert.  
  
## See Also  
 [Alerts Used by Applications and NVAlert](../core/alerts-used-by-applications-and-nvalert2.md)   
 [Network Management with NetView](../core/network-management-with-netview1.md)