---
title: "Estimating Hardware Demands | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 954e8d0b-c19c-488b-badc-da401e57be3f
caps.latest.revision: 4
---
# Estimating Hardware Demands
Use the information in the following table to estimate the amount of processing power required for your Host Integration Server computers.  
  
|Installation category|Hardware guidelines|  
|---------------------------|-------------------------|  
|Approximately 1500–5000 users for each server, with up to 15,000 sessions for each server|A multiprocessor system with at least 128 megabytes (MB) of RAM.<br /><br /> Connections (such as DLC 802.2 or channel) that are fast enough to avoid bottlenecks (recommended). Multiple SNA adapters, except for channel.<br /><br /> Multiple LAN adapters to avoid LAN bottlenecks.<br /><br /> Optionally, dedicated Host Integration Server computers that do not provide file sharing or other LAN services (this depends on the load created by other LAN services).|  
|Up to 600 users for each server (heavy use) or up to 1500 users for each server (light or intermittent use)|A Pentium computer, with at least 128 MB of RAM.<br /><br /> Connections (such as DLC 802.2 or channel) that are fast enough to avoid bottlenecks (recommended). Multiple SNA adapters may be needed, except for channel connections.<br /><br /> Multiple LAN adapters may be needed to avoid LAN bottlenecks.<br /><br /> A more powerful CPU and more RAM may be needed if Host Integration Server computers must support significant additional loads, such as file sharing.|  
|Up to 200 users for each server (heavy use) or up to 500 users for each server (light or intermittent use)|A Pentium computer, with at least 128 MB of RAM.<br /><br /> A more powerful CPU and more RAM may be needed if Host Integration Server computers must support significant additional loads, such as file sharing.|  
|Up to 25 users for each server|A Pentium computer, with at least 128 MB of RAM.<br /><br /> A more powerful CPU and more RAM may be needed if Host Integration Server computers must support significant additional loads, such as file sharing.|  
  
## See Also  
 [Variables Affecting Hardware](../HIS2010/variables-affecting-hardware.md)   
 [Best Practices](../HIS2010/best-practices.md)   
 [Planning Your Hardware](../HIS2010/planning-your-hardware1.md)