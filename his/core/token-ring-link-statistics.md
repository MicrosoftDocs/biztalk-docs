---
title: "Token Ring Link Statistics2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91961d49-ca06-4296-8e76-a8c94a945f42
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# Token Ring Link Statistics
Link statistics are generated when a link is closed or when one of the following counters is about to wrap. Whenever a link statistics message is built, all the counters are reset to 0.  
  
 The NMVT generated has the following format:  
  
|NMVT header||  
|-----------------|------|  
|41 03 8D 00 00 00 00 00|NMVT Header|  
  
|Major vector header||  
|-------------------------|------|  
|00 32|Length of major vector|  
|00 25|Link Statistics major vector|  
  
|Data link traffic counters subvector||  
|------------------------------------------|------|  
|2E9A|Data Link Traffic Counters subvector|  
|04|DLC type: Token Ring|  
|01 or 02|Statistics type: link counter overflow or adapter counter overflow|  
  
|Token ring adapter log information and counters||  
|-----------------------------------------------------|------|  
|*hh*|Adapter number (01+04)|  
|00|Reserved|  
|*hh*|Line error|  
|*hh*|Internal error|  
|*hh*|Burst error|  
|*hh*|ARI/FCI error|  
|*hh*|End delimiter|  
|00|Reserved|  
|*hh*|Lost frame|  
|*hh*|Receive congestion|  
|*hh*|Frame copied error|  
|*hh*|Frequency error|  
|*hh*|Token error|  
|00 00 00|Reserved|  
  
|DLC SAP station information||  
|---------------------------------|------|  
|*hh hh hh hh*|Count of frames transmitted OK|  
|*hh hh hh hh*|Count of frames received OK|  
|*hh hh hh hh*|Count of frames discarded|  
|*hh hh hh hh*|Lost data|  
|*hh hh*|Buffer available in SAP|  
  
|DLC link station information||  
|----------------------------------|------|  
|*hh hh*|Count of I-frames transmitted|  
|*hh hh*|Count of I-frames received|  
|*hh*|Received I-frames error count|  
|*hh*|Transmitted I-frames error count|  
|*hh hh*|T1 timer expired count|  
  
## See Also  
 [Format for Link Statistics](../core/format-for-link-statistics.md)