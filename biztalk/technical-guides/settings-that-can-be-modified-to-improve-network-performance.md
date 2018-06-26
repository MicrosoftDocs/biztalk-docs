---
title: "Settings that can be Modified to Improve Network Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb6aacc3-e697-4cc9-b937-73a2f54e733b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Settings that can be Modified to Improve Network Performance
This topic provides a description of recommended values   that impact network performance.  
  
> [!IMPORTANT]  
>  During performance testing completed for this guide it was observed that Windows Server 2008 appears to be tuned by default. Modification of  registry settings should only be done after a careful analysis of the effects on the system.  
  
## Adjust the MaxUserPort and TcpTimedWaitDelay settings  
 The **MaxUserPort** value controls the maximum port number used when an application requests any available user port from the system. Normally, short-lived ports are allocated in the range from 1025 through 65535. The port range is now truly a range with a starting point and with an endpoint. The new default start port is 49152, and the default end port is 65535. This range is in addition to well-known ports that are used by services and by applications. The port range that is used by the servers can be modified on each server. You adjust this range by using the netsh command, as follows:  
  
 **netsh int \<ipv4&#124;ipv6\> set dynamicport \<tcp&#124;udp\> start=number num=range**  
  
 This command sets the dynamic port range for TCP. The start port is **number**, and the total number of ports is **range**. The following are sample commands: You can view the dynamic port range by using the following netsh commands:  
  
- netsh int ipv4 show dynamicport tcp. To increase the range to the maximum allowed value for tcp v4, use the following command:  
  
   **netsh int ipv4 set dynamicport tcp start=1025 num=64511**  
  
- netsh int ipv4 show dynamicport udp  
  
- netsh int ipv6 show dynamicport tcp  
  
- netsh int ipv6 show dynamicport udp  
  
  The **TcpTimedWaitDelay** value determines the length of time that a connection stays in the TIME_WAIT state when being closed. While a connection is in the TIME_WAIT state, the socket pair cannot be reused. This is also known as the 2MSL state because the value should be twice the maximum segment lifetime on the network. For more information, see [Internet RFC 793](http://go.microsoft.com/fwlink/?LinkId=113719) ( HYPERLINK "<http://go.microsoft.com/fwlink/?LinkId=113719>" <http://go.microsoft.com/fwlink/?LinkId=113719>). To adjust the TcpTimedWaitDelay settings, you have to modify the registry settings as listed below:  
  
###  
  
|||  
|-|-|  
|Key:|HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters|  
|Value:|TcpTimedWaitDelay|  
|Data Type:|REG_DWORD|  
|Range:|30-300 (decimal)|  
|Default value:|0x78 (120 decimal)|  
|Recommended value:|30|  
|Value exists by default?|**No**, needs to be added.|  
  
## See Also  
 [General Guidelines for Improving Network Performance](../technical-guides/general-guidelines-for-improving-network-performance.md)