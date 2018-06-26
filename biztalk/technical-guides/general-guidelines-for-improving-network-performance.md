---
title: "General Guidelines for Improving Network Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 286c10d2-9262-4e3c-adde-f7b5780c2736
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# General Guidelines for Improving Network Performance
Adjusting network settings to optimal values has been shown to effectively address network bottlenecks and improve overall network performance in BizTalk Server solutions. This should be done on all computers involved in the solution, including BizTalk Server computers, SQL Server computers, and any other server computers.  
  
> [!NOTE]  
>  The most common indicator that Network IO is a bottleneck in a BizTalk Server environment is the counter “SQL Server:Wait Statistics\Network IO waits”. When the value for **Avg Wait Time** in this counter is greater than zero on one or more of your SQL Server computers, then Network IO is a bottleneck.  
  
 The following recommendation can be used to increase network performance:  
  
## Add additional network cards to computers in the BizTalk Server environment  
 Just as adding additional hard drives can improve disk performance, adding additional network cards can improve network performance. If the network cards on the computers in your BizTalk Server environment are saturated and the card is a bottleneck, consider adding one or more additional network cards to improve performance.  
  
## Implement network segmentation  
 Follow the recommendations in the **Subnets** section of the ["BizTalk Server Database Optimization" whitepaper](http://go.microsoft.com/fwlink/?LinkID=101578) (http://go.microsoft.com/fwlink/?LinkID=101578).  
  
## Where possible, replace hubs with switches  
 Switches contain logic to directly route traffic between the source and destination whereas hubs use a broadcast model to route traffic. Therefore switches are more efficient and offer improved performance.  
  
## Remove unnecessary network protocols  
 Windows Server computers sometimes have more network services and protocols installed than are actually required. Each additional network client, service or protocol places additional overhead on system resources.  
In addition, each installed protocol generates network traffic. By removing unnecessary network clients, services and protocols, system resources are made available for other processes, excess network traffic is avoided and the number of network bindings that must be negotiated is reduced to a minimum.  
To see the currently installed network clients, protocols and services, follow these steps:  
  
1. Click **Start**, and then click **Control Panel**.  
  
2. In Control Panel, do one of the following  
  
   1.  In **Adjust your computer’s settings**, set **View by** to **Category**, click **Network and Internet**, and then click **Network and Sharing Center**.  
  
   2.  In **Adjust your computer’s settings**, set **View by** to either **Large icons** or **Small icons**, and then click **Network and Sharing Center**.  
  
3. In the Tasks pane, click **Change adapter settings**.  
  
4. Right-click **Local Area Connection** (or the entry for your network connection), and then click **Properties** to display the properties dialog box for the network connection.  
  
5. To remove an unnecessary item, select it and click **Uninstall**. To disable an item, simply clear the checkbox associated with the item.  
  
   If you are unsure about the effects of uninstalling an item for the connection, then disable the item rather than uninstalling it. Disabling items allows you to determine which services, protocols and clients are actually required on a system. When it has been determined that disabling an item has no adverse affect on the server, the item can then be uninstalled.  
   In many cases, only the following three components are required for operation on a standard TCP/IP based network:  
  
-   Client for Microsoft Networks  
  
-   File and Printer Sharing for Microsoft Networks  
  
-   Internet Protocol (TCP/IP)  
  
## Network adapter drivers on all computers in the BizTalk Server environment should be tuned for performance  
  
> [!IMPORTANT]  
>  Before applying tuning to network adapter drivers always install the latest network adapter device drivers for the network cards in the environment.  
  
 Adjust the network adapter device drivers to maximize the amount of memory available for packet buffering, both incoming and outgoing. Also maximize buffer counts, especially transmit buffers and coalesce buffers. The default values for these parameters, and whether they are even provided, vary between manufacturers and driver versions. The goal is to maximize the work done by the network adapter hardware, and to allow the greatest possible buffer space for network operations to mitigate network traffic bursts and associated congestion.  
  
> [!NOTE]  
>  Steps to tune network adapter drivers vary by manufacturer.  
  
 Follow these steps to access settings for network adapters:  
  
1. Click **Start** and then click **Control Panel**.  
  
2. In Control Panel, do one of the following:  
  
   1.  In **Adjust your computer’s settings**, set **View by** to **Category**, click **Network and Internet**, and then click **Network and Sharing Center**.  
  
   2.  In **Adjust your computer’s settings**, set **View by** to either **Large icons** or **Small icons**, and then click **Network and Sharing Center**.  
  
3. In the Tasks pane, click **Change adapter settings**.  
  
4. Right-click **Local Area Connection** (or the name of your network connection), and then click **Properties**.  
  
5. On the **Networking** tab, click **Configure**.  
  
6. Click the **Advanced** tab to access properties that can be configured for the network adapter.  
  
   The following properties should be configured for each network adapter in the BizTalk Server environment:  
  
> [!NOTE]  
>  You apply these settings for each physical network adapter, including the individual network adapters within a teamed set of network adapters that are configured for aggregation, load balancing, or fault tolerance. With some teaming software, you might need to apply these settings to the team also. Note that some network adapters are self-tuning and may not offer the option to configure parameters manually.  
  
- **Power Option** – Configure the network adapter driver to prevent power management functionality from turning off the network adapter to save power. This functionality may be useful for client computers but should seldom, if ever, be used on a BizTalk Server or SQL Server computer.  
  
- **Fixed Speed/Duplex (do not use AUTO)** - It is very important that the network speed, duplex, and flow control parameters are set to correspond to the settings on the switch to which they are connected. This will mitigate the occurrence of periodic “auto-synchronization” which may temporarily take connections off-line.  
  
- **Max Coalesce Buffers** - Map registers are system resources used to convert physical addresses to virtual addresses for network adapters that support bus mastering. Coalesce buffers are available to the network driver if the driver runs out of map registers. Set this value as high as possible for maximum performance. On servers with limited physical memory, this may have a negative impact as coalesce buffers consume system memory. On most systems however, the maximum setting can be applied without significantly reducing available memory.  
  
- **Max Transmit/Send Descriptors and Send Buffers** - This setting specifies how many transmit control buffers the driver allocates for use by the network interface. This directly reflects the number of outstanding packets the driver can have in its “send” queue. Set this value as high as possible for maximum performance. On servers with limited physical memory, this may have a negative impact as send buffers consume system memory. On most systems however, the maximum setting can be applied without significantly reducing available memory.  
  
- **Max Receive Buffers** - This setting specifies the amount of memory buffer used by the network interface driver when copying data to the protocol memory. It is normally set by default to a relatively low value. Set this value as high as possible for maximum performance. On servers with limited physical memory, this may have a negative impact as receive buffers consume system memory. On most systems however, the maximum setting can be applied without significantly reducing available memory.  
  
- **All offload options ON** - In almost all cases performance is improved when enabling network interface offload features. Some network adapters provide separate parameters to enable or disable offloading for send and receive traffic. Offloading tasks from the CPU to the network adapter can help lower CPU usage on the server which will improve overall system performance. The Microsoft TCP/IP transport can offload one or more of the following tasks to a network adapter that has the appropriate capabilities:  
  
  -   **Checksum tasks** - The TCP/IP transport can offload the calculation and validation of IP and TCP checksums for sends and receives to the network adapter; enable this option if the network adapter driver provides this capability.  
  
  -   **IP security tasks** - The TCP/IP transport can offload the calculation and validation of encrypted checksums for authentication headers (AH) and encapsulating security payloads (ESP) to the network adapter. The TCP/IP transport can also offload the encryption and decryption of ESP payloads to the network adapter. Enable these options if the network adapter driver provides this capability.  
  
  -   **Segmentation of large TCP packets** - The TCP/IP transport supports large send offload (LSO). With LSO, the TCP/IP transport can offload the segmentation of large TCP packets.  
  
  -   **Stack Offload** – The entire network stack can be offloaded to a network adapter that has the appropriate capabilities. Enable this option if the network adapter driver provides this capability.  
  
- **Wake On LAN disabled (unless being used)** – Configure the network adapter driver to disable wake-on lan functionality. This functionality may be useful for client computers but should seldom if ever be used on a BizTalk Server or SQL Server computer.  
  
  For more information about tuning network adapters for performance, see the **Network Device Settings** section of the ["BizTalk Server Database Optimization" whitepaper](http://go.microsoft.com/fwlink/?LinkID=101578) (http://go.microsoft.com/fwlink/?LinkID=101578).  
  
## See Also  
 [Settings that can be Modified to Improve Network Performance](../technical-guides/settings-that-can-be-modified-to-improve-network-performance.md)