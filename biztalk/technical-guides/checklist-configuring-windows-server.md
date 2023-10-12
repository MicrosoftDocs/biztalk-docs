---
description: "Learn more about: Checklist: Configuring Windows Server"
title: "Checklist: Configuring Windows Server"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Checklist: Configuring Windows Server

This topic lists steps that you should follow when preparing Windows Server for use in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.

- Configure MSDTC for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For more information, go to [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).

- Configure firewall(s) for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This step is only required if one or more firewalls are in place in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.

  For more information, go to:

  - [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md)
  - [How to configure RPC dynamic port allocation to work with firewalls](/troubleshoot/windows-server/networking/configure-rpc-dynamic-port-allocation-with-firewalls)

- Turn off hyperthreading on all computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.

  - It is critical that hyperthreading be turned off for computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This is a BIOS setting, typically found in the Processor settings of the BIOS setup.

    Hyperthreading makes the server appear to have more processors/processor cores than it actually does; however, hyperthreaded processors typically provide between 20% and 30% of the performance of a physical processor/processor core. When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] counts the number of processors to adjust its self-tuning algorithms, the hyperthreaded processors cause these adjustments to be skewed, which is detrimental to overall performance.

  - Hyperthreading should be turned off for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers because applications that can cause high levels of contention (such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]) can cause decreased performance in a hyper-threaded environment on a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.

- Ensure Windows Server processor scheduling is set to “Background services”.

  Ensuring this configuration option is set on all computers running Windows Server in your environment will improve the overall system performance. Follow these steps to ensure Windows Server is configured to favor background services:

  1. Click **Start**, click **Run**, and then type **sysdm.cpl** in the **Run** box.
  2. In the **System Properties** dialog box, click the **Advanced** tab, and then click **Settings** under **Performance**.
  3. In the **Performance Options** dialog box, click the **Advanced** tab, make sure the **Background services** option is selected under **Processor scheduling**, click **OK**, and then click **OK** again to close **System Properties** dialog box.

- Place the Windows paging file on a separate local physical drive. 

  Moving the paging file to a separate physical volume other than the operating system on a computer running Windows Server improves performance by reducing disk contention.

  Follow these steps to move the paging file to a separate physical volume other than the operating system:

  1. Click **Start**, click **Run**, and then type **sysdm.cpl** in the **Open** box.
  2. Click the **Advanced** tab, and then click **Settings** under **Performance**.
  3. Click the **Advanced** tab, click **Change** under **Virtual memory**, specify options for the paging file, click **OK** and then click **OK** again to close System Properties. You must restart the computer for the new settings to take effect.

- Defrag the disks and page file:

  - Defragment all disks (local and SAN/NAS) on a regular basis by scheduling off-hours disk defragmentation.
  - Defragment the Windows paging file and pre-allocate the Master File Tables of each disk in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment to boost overall system performance. 

  Use the [Windows commands: defrag](/windows-server/administration/windows-commands/defrag) to defragment the Windows paging file and pre-allocate the Master File Tables.

- If antivirus software is installed on the computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], disable real-time scanning of the data and transaction files (.mdf, .ndf, .ldf, .mdb).

  Real-time scanning of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] data and transaction files can increase disk I/O contention and reduce [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance.

- If antivirus software is installed on the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], disable real-time scanning of non-executable file types referenced by any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive locations (usually .XML, but can also be .csv, .txt, etc.).

  Real-time scanning of non-executable files that are referenced by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive locations can increase I/O contention on these files and reduce [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance.

- If intrusion detection software is installed, disable network scanning between computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and external data repositories ([!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]) or messaging services (such as Message Queuing and WebSphere MQSeries).

  Intrusion detection software can slow down or even prevent valid communications over the network.

- Network card (NIC) drivers on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment should be tuned for performance.

  Adjust the network device drivers to maximize the amount of memory available for packet buffering, both incoming and outgoing. Also maximize buffer counts, especially transmit buffers and coalesce buffers. The default values for these parameters, and whether they are even provided, vary between manufacturers and driver versions. The goal is to maximize the work done by the network interface card hardware, and to allow the greatest possible buffer space for network operations to mitigate network traffic bursts and associated congestion.

- Set the network cards to a fixed speed and duplex.

  Use a fixed speed and duplex (1 Gigabit or higher with full duplex) for the network connections on the BizTalk and SQL servers. This will ensure that the network interface does not auto-negotiate a lower speed or duplex setting, which has been a problem with some enterprise switches in the past. Also, in high-volume environments, it is advisable to have Gigabit networks.

- Stop or disable any Windows services that are not strictly necessary (such as Print Spooler and Indexing Service) on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.

  Running unnecessary services on a production server uses system resources which could otherwise be used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].

## In This Section

- [Installing COM+ Hotfix Rollup Packages](installing-com-hotfix-rollup-packages.md)

## See Also

[Operations Checklists](operations-checklists.md)
