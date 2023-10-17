---
description: "Learn more about: SDLC Alert Local Logging"
title: "SDLC Alert Local Logging1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d43d22b3-3a8b-4fcd-978c-151ec7aadeb0
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# SDLC Alert Local Logging
Before [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] attempts to build and send an SDLC link alert, information about the outage that caused the alert is recorded in a log file that can be viewed using the Windows Event Log service. Message 182 is always logged, as follows:  
  
```  
182I:  Connection failure, code = (outagecode)  
Cause Data                          = hh...hh  
Link Role                           = hh  
Remote Node Type                    = hh  
```  
  
 The Outage Code (outagecode) is also reported on Message 23. For a complete list of these codes, the conditions they represent, and the specific link alerts on which they are used, see the next section.  
  
 Cause Data is a list of the failure causes from the Failure causes subvector in the alert. Link Role and Remote Node type are as described in the Link Connection Subsystem Configuration Data subvector in the alert.  
  
 A connection failure can be due to a station outage, rather than a link outage. If it is due to a station outage  which can be recognized by outage code values of X'80' or higher  then Message 183, formatted as follows, is also logged:  
  
```  
183I:  
Detailed diagnostic data for station (stationaddress):  
SBSY   CFTX   CFRX   V(S)   V(R)   N(R)   OSFC   T1CT  
hh   hhhh   hhhh   hh     hh     hh     hh     hhhh  
```  
  
 The value (stationaddress) is the station address as given in the Detail qualifier subvector in the alert.  
  
 The other fields are all data from the Link Station Data subvector, as follows:  
  
|Field|Description|  
|-----------|-----------------|  
|SBSY|Link station state: 80 or 40|  
||(local or remote station sending RNR)|  
|CFTX|Last SDLC control field sent|  
|CRX|Last SDLC control field received|  
|V(S)|N(S) count|  
|V(R)|N(R) count|  
|N(R)|Last received N(R)|  
|OSFC|Outstanding frame count|  
|T1CT|Reply timer expiration count|  
  
## In this Section  
 [Identifying Alerts from Local Logs Only](../core/identifying-alerts-from-local-logs-only1.md)  
  
## See Also  
 [Link Alerts for SDLC and Token Ring](../core/link-alerts-for-sdlc-and-token-ring2.md)
