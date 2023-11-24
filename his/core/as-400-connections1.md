---
description: "Learn more about: IBM System i Connections"
title: "AS-400 Connections1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# IBM System i Connections
Network Name and Control Point Name (used together and called the fully qualified name) are the identifiers used when using exchange identification (XID) with IBM System i computers. Check to make sure that the following items match; if they do not, Host [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] is not identifying itself in a way that the IBM System i can recognize.  
  
|Identifier used on IBM System i|Identifier to configure<br /><br /> on Host Integration Server|  
|--------------------------------|------------------------------------------------------------|  
|**RMTNETID** (usually; often set to APPN); **RMTCPNAME**|**Local Network Name** and **Local Control Point Name** (configured on the server)|  
|**RMTNETID** (often set to APPN); **CP Name** (shown in the **Display network attributes** screen)|**Remote Network Name** and **Remote Control Point Name** (configured on the connection)|  
  
 Event log entries can be very helpful in diagnosing and correcting mismatched identifiers between Host Integration Server and host computers.  
  
## See Also  
 [Host Configuration](../core/host-configuration1.md)
