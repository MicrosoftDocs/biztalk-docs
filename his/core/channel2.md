---
description: "Learn more about: Channel"
title: "Channel2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Channel
Channel connections provide direct channel attachment to a mainframe. There are two types of channel connections: older Bus & Tagchannel connections, which can reach speeds of up to 4.5 megabytes per second (MBps), and newer ESCON connections, which can reach speeds approaching 17 MBps. Support for channel connections is limited to adapters supported natively through Host Integration Server.  
  
 Enterprise System Connection (ESCON) channel attachments use standard fiber cable and increase throughput significantly.  
  
 ESCON is an ideal connection method in centralized or distributed deployments where high performance and responsiveness are required.  
  
 The following table summarizes all common connection methods that can be used with Host Integration Server.  
  
|Method|Throughput|Characteristics|  
|------------|----------------|---------------------|  
|Token Ring|4 or 16 MBps|Midrange performance using data link control (DLC) protocol<br /><br /> Supports multiple host connections using a single adapter<br /><br /> Uncomplicated and inexpensive to implement<br /><br /> Suitable for a wide range of purposes|  
|Ethernet|10 GBps|Midrange performance using DLC protocol<br /><br /> Supports multiple host connections using a single adapter<br /><br /> Uncomplicated and inexpensive to implement<br /><br /> Suitable for light to medium network traffic conditions|  
|FDDI|100 MBps|High performance using DLC protocol<br /><br /> Supports multiple host connections using a single adapter<br /><br /> Relatively expensive to implement<br /><br /> Suitable for higher-performance connections|  
|SDLC|9600–19200 bits per second (BPS)|Low performance using SDLC protocol<br /><br /> Supports 256 sessions over a single host connection<br /><br /> Uncomplicated and inexpensive to implement<br /><br /> Suitable for low-traffic WAN connections|  
|Channel: Bus & Tag|4.5 MBps|High performance<br /><br /> Supports a high number of host connections.<br /><br /> More expensive<br /><br /> Suitable for high-performance connections|  
|Channel: ESCON|17 MBps|Highest performance<br /><br /> Supports a high number of host connections<br /><br /> More expensive<br /><br /> Suitable for conditions where maximum throughput is required|  
  
## See Also  
 [Connection Methods](../core/connection-methods2.md)   
 [Synchronous Data Link Control (SDLC)](../core/synchronous-data-link-control-sdlc-1.md)
