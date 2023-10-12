---
description: "Learn more about: SDLC Link Statistics"
title: "SDLC Link Statistics1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SDLC Link Statistics
Link statistics are generated when a link is closed or when one of the wrap counters listed later in this section is about to wrap. Whenever a link statistics message is built, all the wrap counters are reset to 0. The cumulative counters are not reset; they provide statistics from the point at which the particular link service was started.  
  
 The NMVT generated has the following format:  
  
|NMVT header|Description|  
|-----------------|------|  
|41 03 8D 00 00 00 00 00|NMVT Header|  
  
|Major vector header|Description|  
|-------------------------|------|  
|00 69|Length of major vector|  
|00 25|Link statistics major vector|  
  
|Data link traffic counters subvector|Description|  
|------------------------------------------|------|  
|65 9A|Data Link Traffic Counters subvector|  
|03|DLC type: SDLC|  
|*hh*|Adapter number (01+04)|  
  
|Date/time link established|Description|  
|---------------------------------|------|  
|*hh*|Date|  
|*hh*|Month|  
|*hh* *hh*|Year|  
|*hh*|Hour|  
|*hh*|Minute|  
|*hh*|Second|  
|*hh*|Hundredths of a second|  
|*hh*|Counter|  
  
|Wrap counters|Description|  
|-------------------|------|  
|*hh*|Transmit I-frames OK|  
|*hh*|Transmit I-frames not OK|  
|*hh*|Retransmit I-frames|  
|*hh*|Received I-FCS OK|  
|*hh*|Received I-FCS not OK|  
|*hh*|Total frames sent|  
|00|Reserved|  
|*hh*|Lost data frames received|  
|*hh*|FRMR conditions sent|  
|00|Reserved|  
|*hh*|CTS drop|  
|00|Reserved|  
|00|Reserved|  
|*hh*|DSR drop out|  
|*hh*|Inactivity timeouts|  
|00|Reserved|  
|*hh*|DMA underruns|  
|00|Reserved|  
|*hh*|Transmit fail timeouts|  
|00|Reserved|  
  
## Cumulative Counters  
 The cumulative counters are the same counters as the wrap counters, with reserved bytes in the same positions.  
  
## See Also  
 [Format for Link Statistics](../core/format-for-link-statistics1.md)
