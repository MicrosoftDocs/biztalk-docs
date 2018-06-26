---
title: "Network Optimizations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9ff0392f-37ae-4ca6-8cc6-d53065de64c5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Network Optimizations
In a BizTalk Server environment where the BizTalk Server computer(s) are separate from the SQL Server computer(s), each and every message processed by BizTalk Server requires communication over the network. This communication includes considerable traffic between the BizTalk Server computers and the BizTalk Message Box database(s), the BizTalk Management database(s), the BAM databases, and other databases. In high-load scenarios, this communication can result in considerable network traffic and can become a bottleneck, especially when network settings have not been optimized, not enough network interface cards are installed, or insufficient network bandwidth is available.  
  
 This topic provides steps for improving networking performance between Hyper-V virtual machines running on the same Hyper-V host computer and provides some general recommendations for improving network performance.  
  
> [!NOTE]  
>  The most common indicator that Network IO is a bottleneck is the counter “SQL Server:Wait Statistics\Network IO waits.” When the value for **Avg Wait Time** in this counter is greater than zero on one or more of your SQL Server computers, then Network IO is a bottleneck.  
  
## Improving Network Performance of BizTalk Server on Hyper-V  
  
### Configure Hyper-V Virtual Machines that are Running on the same Hyper-V host computer to use a Private Virtual Network  
 To improve networking performance between Hyper-V virtual machines that are running on the same Hyper-V host computer, create a private virtual network and route network traffic between virtual machines through the private virtual network.  
  
##### Create a Private Virtual Network  
  
1.  Click **Start**, click **All Programs**. Click **Administrative Tools**, and then click **Hyper-V Manager**.  
  
2.  In the left-hand pane of the Hyper-V Manager, right-click **Hyper-V Manager**, and then click **Connect to Server**.  
  
3.  In the **Select Computer** dialog box, enter the name of the Hyper-V host computer, and then click **OK**.  
  
4.  In the left-hand pane of the Hyper-V Manager, right-click the Hyper-V host, and then click **Virtual Network Manager**.  
  
5.  In the Virtual Network Manager, under **What type of virtual network do you want to create?**, click **Private**, and then click **Add**.  
  
6.  Enter a name for the new virtual network, and then click **OK**. The virtual network is now available to each Hyper-V virtual machine that is run on this Hyper-V host.  
  
##### Add the Private Virtual Network to Hyper-V Virtual Machines running on the Hyper-V Host  
  
1.  Click **Start**, click **All Programs**. Click **Administrative Tools**, and then click **Hyper-V Manager**.  
  
2.  In the left-hand pane of the Hyper-V Manager, right-click **Hyper-V Manager**, and then click **Connect to Server**.  
  
3.  In the **Select Computer** dialog box, enter the name of the Hyper-V host computer, and then click **OK**.  
  
4.  Shut down any running virtual machines for which you would like to add the private virtual network by right-clicking on the virtual machine, and then clicking **Shut down**.  
  
5.  After shutting down the virtual machines, right-click a virtual machine, and then click **Settings** to change the settings for a virtual machine.  
  
6.  In the **Settings for <machine_name>** dialog box, under **Add Hardware**, click to select **Network Adapter**, and then click **Add**.  
  
7.  On the **Network Adapter** configuration page, under **Network:**, select the private virtual network that you created earlier, and then click **OK**. You have now made the private virtual network available to the Hyper-V virtual machine which will be accessible the next time that the virtual machine is started.  
  
8.  Repeat the steps above for each virtual machine for which you want to route network traffic through the private virtual network.  
  
9. Start the virtual machines that you have added the private virtual network to. Right click each virtual machine and click **Start**.  
  
##### Configure each Virtual Machine to use the Private Virtual Network  
  
1.  Once each virtual machine has been started, the private virtual network is accessible to the virtual machine as a network connection. Configure the network connection on each virtual machine to use TCP/IPv4, and specify settings for the TCP/IPv4 protocol.  
  
    1.  Access the network connection properties page, select **Internet Protocol Version 4(TCP/IPv4)**, and then click **Properties**.  
  
    2.  Click the radio button next to **Use the following IP address**.  
  
2.  Enter a value for the **IP address** field from the range of private IP addresses identified in “RFC 1918, Address Allocation for Private IP Addresses” at [http://go.microsoft.com/fwlink/?LinkID=31904](http://go.microsoft.com/fwlink/?LinkID=31904).  
  
3.  Make a note of the IP address that you specified; you will need to associate this value with the NetBIOS name of this computer in a HOSTS file entry later.  
  
4.  Enter an appropriate value for the **Subnet mask** field.  
  
    > [!NOTE]  
    >  Windows should populate the **Subnet mask** field with an appropriate value based upon the value that you entered into the **IP address** field.  
  
5.  Leave the **Default gateway** field blank, click **OK**, and then click **Close**.  
  
6.  After configuring each virtual machine with a unique private IP address, update the HOSTS file on each virtual machine with the IP address and NetBIOS name of the other virtual machines running on the Hyper-V host computer. The updated HOSTS file should be saved to the %systemroot%\drivers\etc\ folder on each virtual machine.  
  
    > [!NOTE]  
    >  Because by default Windows checks the local HOSTS file first to resolve NetBIOS names, by updating the HOSTS file on each virtual machine with the unique private IP addresses of the other virtual machines, network traffic between these machine will now be routed over the private virtual network.  
  
### Disable TCP Offloading for the Virtual Machine Network Cards  
 Edit the registry as described in the MSDN topic “Using Registry Values to Enable and Disable Task Offloading (NDIS 5.1)” at [http://go.microsoft.com/fwlink/?LinkId=147619](http://go.microsoft.com/fwlink/?LinkId=147619) to disable TCP offloading for the network cards on each virtual machine.  
  
> [!IMPORTANT]  
>  Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system. Use Registry Editor at your own risk. For more information about how to back up, restore, and modify the registry, see the Microsoft Knowledge Base article "Description of the Microsoft Windows registry" at [http://go.microsoft.com/fwlink/?LinkId=62729](http://go.microsoft.com/fwlink/?LinkId=62729).  
  
## General guidelines for improving network performance  
 The following recommendations can be used to increase network performance:  
  
### Add additional network cards to computers in the BizTalk Server environment  
 Just as adding additional hard drives can improve disk performance, adding additional network cards can improve network performance. If the network cards on the computers in your BizTalk Server environment are saturated and the card is a bottleneck, consider adding one or more additional network cards to improve performance.  
  
### Implement network segmentation  
 Follow the recommendations in the **Subnets** section of the "BizTalk Server Database Optimization" whitepaper at [http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578).  
  
### Where possible, replace hubs with switches  
 Switches contain logic to directly route traffic between the source and destination whereas hubs use a broadcast model to route traffic. Therefore switches are more efficient and offer improved performance.  
  
### Remove unnecessary network protocols  
 Windows Server computers sometimes have more network services and protocols installed than are actually required. Each additional network client, service or protocol places additional overhead on system resources.  
  
 In addition, each installed protocol generates network traffic. By removing unnecessary network clients, services and protocols, system resources are made available for other processes, excess network traffic is avoided and the number of network bindings that must be negotiated is reduced to a minimum.  
  
 To see the currently installed network clients, protocols and services, follow these steps:  
  
1. Click **Start**, point to **Settings**, and then click **Control Panel**.  
  
2. Double-click **Network Connections** to display the network connections on the computer.  
  
3. Right-click **Local Area Connection** (or the entry for your network connection), and then click **Properties** to display the properties dialog box for the network connection.  
  
4. To remove an unnecessary item, select it and click **Uninstall**. To disable an item, simply clear the checkbox associated with the item.  
  
   If you are unsure about the effects of uninstalling an item for the connection, then disable the item rather than uninstalling it. Disabling items allows you to determine which services, protocols and clients are actually required on a system. When it has been determined that disabling an item has no adverse affect on the server, the item can then be uninstalled.  
  
   In many cases, only the following three components are required for operation on a standard TCP/IP based network:  
  
-   Client for Microsoft Networks  
  
-   File and Printer Sharing for Microsoft Networks  
  
-   Internet Protocol (TCP/IP)  
  
### Network adapter drivers on all computers in the BizTalk Server environment should be tuned for performance  
  
> [!IMPORTANT]  
>  Before applying tuning to network adapter drivers, always install the latest network adapter device drivers for the network cards in the environment.  
  
 Adjust the network adapter device drivers to maximize the amount of memory available for packet buffering, both incoming and outgoing. Also maximize buffer counts, especially transmit buffers and coalesce buffers. The default values for these parameters, and whether they are even provided, vary between manufacturers and driver versions. The goal is to maximize the work done by the network adapter hardware, and to allow the greatest possible buffer space for network operations to mitigate network traffic bursts and associated congestion.  
  
> [!NOTE]  
>  Steps to tune network adapter drivers vary by manufacturer.  
  
 Follow these steps to access settings for network adapters in[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]:  
  
1. Click **Start**, , and then click **Control Panel**.  
  
2. Click **Network and Internet**, and then click **Network and Sharing Center**.  
  
3. Click **Change adapter settings**, Right-click **Local Area Connection** (or the name of your network connection), and then click **Properties**.  
  
4. On the **General** tab, click **Configure**.  
  
5. Click the **Advanced** tab to access properties that can be configured for the network adapter.  
  
   The following properties should be configured for each network adapter in the BizTalk Server environment:  
  
> [!NOTE]  
>  You apply these settings for each physical network adapter, including the individual network adapters within a teamed set of network adapters that are configured for aggregation, load balancing, or fault tolerance. With some teaming software, you might need to apply these settings to the team also. Note that some network adapters are self-tuning and may not offer the option to configure parameters manually.  
  
- **Power Option** – Configure the network adapter driver to prevent power management functionality from turning off the network adapter to save power. This functionality may be useful for client computers but should seldom, if ever, be used on a BizTalk Server or SQL Server computer.  
  
- **Fixed Speed/Duplex (do not use AUTO)** - It is very important that the network speed, duplex, and flow control parameters are set to correspond to the settings on the switch to which they are connected. This will mitigate the occurrence of periodic “auto-synchronization” which may temporarily take connections off-line.  
  
- **Max Coalesce Buffers** - Map registers are system resources used to convert physical addresses to virtual addresses for network adapters that support bus mastering. Coalesce buffers are available to the network driver if the driver runs out of map registers. Set this value as high as possible for maximum performance. On servers with limited physical memory, this may have a negative impact as coalesce buffers consume system memory. On most systems however, the maximum setting can be applied without significantly reducing available memory.  
  
- **Max Transmit/Send Descriptors and Send Buffers** - This setting specifies how many transmit control buffers the driver allocates for use by the network interface. This directly reflects the number of outstanding packets the driver can have in its “send” queue. Set this value as high as possible for maximum performance. On servers with limited physical memory, this may have a negative impact as send buffers consume system memory. On most systems however, the maximum setting can be applied without significantly reducing available memory.  
  
- **Max Receive Buffers** - This setting specifies the amount of memory buffer used by the network interface driver when copying data to the protocol memory. It is normally set by default to a relatively low value. Set this value as high as possible for maximum performance. On servers with limited physical memory, this may have a negative impact as receive buffers consume system memory. On most systems however, the maximum setting can be applied without significantly reducing available memory.  
  
- **All offload options ON** - In almost all cases performance is improved when enabling network interface offload features. Some network adapters provide separate parameters to enable or disable offloading for send and receive traffic. Offloading tasks from the CPU to the network adapter can help lower CPU usage on the server which will improve overall system performance. The Microsoft TCP/IP transport can offload one or more of the following tasks to a network adapter that has the appropriate capabilities:  
  
  -   **Checksum tasks** - The TCP/IP transport can offload the calculation and validation of IP and TCP checksums for sends and receives to the network adapter, enable this option if the network adapter driver provides this capability.  
  
  -   **IP security tasks** - The TCP/IP transport can offload the calculation and validation of encrypted checksums for authentication headers (AH) and encapsulating security payloads (ESP) to the network adapter. The TCP/IP transport can also offload the encryption and decryption of ESP payloads to the network adapter. Enable these options if the network adapter driver provides this capability.  
  
  -   **Segmentation of large TCP packets** - The TCP/IP transport supports large send offload (LSO). With LSO, the TCP/IP transport can offload the segmentation of large TCP packets.  
  
  -   **Stack Offload** – The entire network stack can be offloaded to a network adapter that has the appropriate capabilities. Enable this option if the network adapter driver provides this capability.  
  
- **Wake On LAN disabled (unless being used)** – Configure the network adapter driver to disable wake-on lan functionality. This functionality may be useful for client computers but should seldom if ever be used on a BizTalk Server or SQL Server computer.  
  
  For more information about tuning network adapters for performance, see the **Network Device Settings** section of the "BizTalk Server Database Optimization" whitepaper at [http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578).