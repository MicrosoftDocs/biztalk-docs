---
description: "Learn more about: System Monitor Overview"
title: "System Monitor Overview1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# System Monitor Overview
Using the Windows System Monitor, you can view reports on CPU load, memory usage, and interrupt rate, as well as the overall throughput of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] traffic on the network. Restrained use of the system monitor is recommended because the tool itself can cause extra stress on the servers CPU. Specifically, this can happen if tracking all the details of many logical units (LUs) over the network from another server. Try to limit the system monitor to providing summary statistics only.  
  
 Also, try to check the CPU loads of your receiver servers and stress client computers during a practice run to make sure they are not overloaded. If the client computers are Windows computers, you can use the System Monitor application in Windows to check the CPU load on the client machines.  
  
 Host Integration Server services are fully integrated with the Windows operating system. This allows the services, connections, and processes associated with Host Integration Server to be assigned to the System Monitor. You can evaluate the demand and performance of one or more Host Integration Server-based computers to obtain a benchmark and to estimate hardware requirements for future growth.  
  
 You can use the Windows System Monitor to look at the resource use of specific components and program processes. With the system monitor, you can create charts and reports that gauge a computer's efficiency; identify and troubleshoot possible problems such as unbalanced resource use, insufficient hardware, or poor program design; and plan for additional hardware needs.  
  
 Using the System Monitor, you can configure object counters and instances to assist in evaluating Host Integration Server performance. Specific counters and instances appear when a particular service is installed and running on the server.  
  
 For detailed instructions about using the System Monitor, see your Windows Server documentation.  
  
## See Also  
 [Useful Performance Counters](../core/useful-performance-counters2.md)   
 [Performance Counters on Transaction Integrator](../core/performance-counters-on-transaction-integrator2.md)   
 [Maximizing Communications Throughput](../core/maximizing-communications-throughput2.md)   
 [How to Start System Monitor](../core/how-to-start-system-monitor1.md)   
 [How to Configure System Monitor](../core/how-to-configure-system-monitor1.md)   
 [How to Save Performance Data](../core/how-to-save-performance-data1.md)   
 [System Monitor](../core/system-monitor1.md)
