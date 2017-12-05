---
title: "Indicating Lost RTM Data2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a20ae2d-b04d-40b4-97c6-97ac360ac318
caps.latest.revision: 3
---
# Indicating Lost RTM Data
When [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] sends response time monitor (RTM) data to the host, it can indicate to the host that RTM data may have been lost, that is, some host response times were not included in the RTM data sent to the host. This indication is sent when:  
  
-   One of the RTM counters reaches its maximum value, and [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is not configured to send RTM data unsolicited at counter overflow. When this occurs, Host Integration Server stops recording response times until the host requests the data or until end-of-session, if unsolicited sending at end-of-session is configured. The data is sent with an indication that data may have been lost due to counter overflow.  
  
-   Connection to the host for either Host Integration Server or the Windows servers ends abnormally. The first RTM data sent to the host after the connection is re-established includes the lost-data indicator to indicate that data may have been lost due to failure of the server.  
  
-   Host Integration Server is configured to send RTM data at the end-of-session, and a new 3270 session is started before the RTM data for the previous 3270 session on the same LU can be sent. Response times for the new session are discarded until the RTM data from the previous session is sent and the counters are reset. When RTM data is sent on the new session, it includes the lost data indicator.  
  
## See Also  
 [Defining RTM Thresholds](../core/defining-rtm-thresholds1.md)   
 [Specifying When RTM Data is Sent](../core/specifying-when-rtm-data-is-sent2.md)