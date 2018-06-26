---
title: "Installing and Configuring a Hyper-V Virtual Machine for use with BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 86add392-3cde-432d-95d6-c81d68716537
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing and Configuring a Hyper-V Virtual Machine for use with BizTalk Server
This topic provides recommendations for installing and configuring BizTalk Server in a Hyper-V environment, including recommendations for installation and configuration of the Hyper-V virtual machine and recommendations for installing BizTalk Server on a Hyper-V virtual machine.  

## Installing and Configuring Hyper-V  
 Before installing Hyper-V, see [What's New in Hyper-V in Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkID=202427). The “Microsoft Hyper-V Server 2008 R2 Getting Started” guide provides details about how to install and configure [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] Hyper-V. The guide is available at [http://go.microsoft.com/fwlink/?LinkID=202431](http://go.microsoft.com/fwlink/?LinkID=202431).  

 “The Performance Tuning Guidelines for Windows Server 2008 R2” document provides details on tuning [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and includes a section specifically focused on Hyper-V. The document is available at [http://go.microsoft.com/fwlink/?LinkID=202087](http://go.microsoft.com/fwlink/?LinkID=202087).  

### Hyper-V Platform Prerequisites  
 Hyper-V is a server role available for 64-bit and all editions of  [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] are 64-bit only. Additionally, the physical hardware must support hardware assisted virtualization. This means the processor must be compatible with Intel Virtualization Technology (Intel VT) or AMD Virtualization (AMD-V) technology, the system BIOS must support Data Execution Prevention (DEP), and DEP must be enabled. Specifically, you must enable the Intel XD bit (execute disable bit) or AMD NX bit (no execute bit).  

> [!NOTE]  
>  After enabling these options in the system BIOS, turn off the computer completely and then restart the computer to ensure that these settings are applied.  

#### Determining Hardware Requirements  
 Due to the demands of server consolidation, Hyper-V servers tend to consume more CPU and memory, and require greater disk I/O bandwidth than physical servers with comparable computing loads. In order to deploy an environment that will meet expectations, consider the factors below to determine the exact hardware requirements of your server.  

##### Storage Configuration Options  
 The storage hardware should provide sufficient I/O bandwidth and storage capacity to meet the current and future needs of the virtual machines that you plan to host. There is a trade-off when choosing the storage configuration for Hyper-V between capacity usage and the performance it can provide.  

 When planning storage configuration, consider the requirements of the environment you are provisioning. The requirements for production, pre-production, and development environments may differ considerably.  

 If you are deploying a production BizTalk Server environment on Hyper-V, performance will be a key requirement. To avoid disk I/O contention on busy production systems, install integration services on both the host and guest operating system and configure disks for data volumes with the synthetic SCSI controller. For highly intensive storage I/O workloads that span multiple data drives, each VHD should be attached to a separate synthetic SCSI controller for better overall performance. In addition, each VHD should be stored on separate physical disks. For more information about configuring disks for data volumes with the synthetic SCSI controller see the “Optimize Disk Performance” section of the topic [Checklist: Optimizing Performance on Hyper-V](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md).  

 Typically, development environments do not have stringent performance requirements since maximizing resource utilization tends to be the main priority. For development environments the performance provided when hosting multiple VHD files on a single physical drive is generally acceptable.  

 Hyper-V supports several different types of storage disk options. Each of the storage options can be attached via an IDE or SCSI controller to the machine. A potential benefit of using the SCSI controller over the IDE controller is that it will only work correctly if the correct versions of the operating system integration components have been installed on the guest virtual machine. This is a straightforward method for ensuring that correct operating system integration components are installed on the guest operating system.  

> [!NOTE]  
>  Unlike previous versions of Microsoft virtualization technology, there is no performance difference between using a virtual IDE controller or a virtual SCSI controller when accessing virtual hard disks.  

 For intensive read-write activities, such as hosting [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases, the passthrough disk option provides incremental performance advantages over fixed virtual hard drive (VHD) disks. The passthrough option permits the virtual machine to have direct access to the physical disk and bypasses the NTFS file system in the root partition but does not support certain functionality of virtual disks, such as Virtual machine snapshots and clustering support. Therefore use of the passthrough disk feature is not recommended in a BizTalk or SQL Server environment because the marginal performance benefits are more than offset by the missing functionality.  

 The following table summarizes the advantages and disadvantages of available Hyper-V storage options:.  


|    **Hyper-V Storage Type**     |                                                                                                                                                                                                      **Pros**                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                              **Cons**                                                                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                                     **Considerations for BizTalk Server**                                                                                                                                                                                                                                                      |
|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Fixed size disks**       | Performs better than a dynamic VHD because the VHD file is initialized at its maximum possible size when it is created on the physical hard drive.<br /><br /> This makes fragmentation less likely and, therefore, mitigates scenarios where a single I/O is split into multiple I/Os. This has the lowest CPU overhead of the VHD types because reads and writes do not need to look up the mapping of the block. |                                                                                                                                                                                                                                                                                                                                                                   Requires allocation of the full amount of disk space up-front.                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                   Use for operating system volumes on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. **Important:**  The startup disk of a Hyper-V guest partition must be attached to an IDE contoller.                                                                                                                   |
| **Dynamically expanding disks** |                                                                                                        The size of the VHD file increases to the size specified when creating the disk, as more data is stored on the virtual machine itself. This accommodates the most efficient use of available storage.                                                                                                        | Does not perform as well as a fixed size VHD. This is because the blocks in the disk start as zeroed blocks but are not backed by any actual space in the VHD file. Reads from such blocks return a block of zeros. When a block is first written to, the virtualization stack must allocate space within the VHD file for the block and then update the corresponding metadata. In addition to this every time an existing block is referenced the block mapping must be looked up in the metadata. This increases the number of read and write activities which in turn causes increased CPU utilization.<br /><br /> The dynamic growth also requires that the server administrator monitor disk capacity to ensure that there is sufficient disk storage as the storage requirements increase. |                                                                                                                               Does not perform as well as a fixed size VHD.<br /><br /> If performance is not a concern, for instance in a development environment, this may be a suitable option for the operating system hard drives.<br /><br /> Causes additional CPU overhead due to block mapping lookup.                                                                                                                                |
|     **Differencing disks**      |                                                                               This a parent-child configuration where the differencing disk stores all changes relative to a base VHD and the base VHD remains static. Therefore only the blocks which are different from the parent need to be stored in the child differencing VHD.                                                                               |                                                                                                                                                                                                                                                                                                          Performance can degrade because read/writes need to access the fixed/dynamic parent VHD as well as the differencing disk. This increases CPU utilization and disk I/O overhead.                                                                                                                                                                                                                                                                                                           |                                                                                                                     A large amount of machine specific configuration is required for BizTalk Server installations and child VHD files may grow substantially which would minimize the benefits of using this disk configuration. Reading from multiple VHD’s in this scenario incurs additional CPU and disk I/O overhead.                                                                                                                     |
|      **Passthrough disks**      |                                                                                                                               These are physical disks which are set to *offline* in the root partition and enable Hyper-V to have exclusive read-write access to the physical disk.                                                                                                                                |                                                                                                                                                                                                                                                                                                        Requires a fully dedicated disk or LUN in order for it to be allocated to a virtual machine.<br /><br /> A physical disk is more difficult to move between machines than VHD files.                                                                                                                                                                                                                                                                                                         | If your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance is running on a Hyper-V, you may obtain incremental performance improvements by using passthrough disks over using fixed virtual hard disks (VHD) for the BizTalk Server data volumes.<br /><br /> If you are hosting local file receive locations on BizTalk Server or streaming large messages to disk during processing, you may obtain incremental performance improvements using passthrough disks over using fixed virtual hard disks (VHD). |

 For more information about implementing disks and storage with Hyper-V see [Implementing Disks and Storage](http://go.microsoft.com/fwlink/?LinkID=142362) (http://go.microsoft.com/fwlink/?LinkID=142362).  

##### Networking  
 BizTalk Server tends to exhibit high network utilization. Therefore, when network performance is an issue, consider allocating a separate physical network card for each virtual machine.  

 When configuring a virtual machine, ensure that you use the Network Adapter instead of the Legacy Network Adapter. The legacy network adapter is intended for operating systems that do not support integration components.  

 To measure network performance use the **“\Network Interface \Bytes Total/sec”** and the **\Network Interface(\*)\Output Queue Length** performance monitor counters on the host operating system to measure overall performance of the network card. If a physical network has been identified as being busy, use the **“\Hyper-V Virtual Network Adapter (\*)\Bytes/sec”** counter on the host operating system to identify which virtual machine network adapter(s) is/are generating high load.  

 For more information about evaluating network performance on a Hyper-V environment see the **Measuring Network Performance** section of [Checklist: Measuring Performance on Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).  

##### CPU  
 Hyper-V supports different numbers of virtual processors for different guest operating systems; as summarized in the table below. To allocate the maximum CPU resources for BizTalk Server, install it on a [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] guest operating system,  which supports four virtual processors per virtual machine.  

 Configure a 1-1 allocation of virtual processors in the guest operating system(s) to logical processors available to the host operating system to prevent excessive context switching. Excessive context switching between processors will result in performance degradation. For more information about allocating virtual processors to logical processors, see the “Optimize Processor Performance” section of the topic [Checklist: Optimizing Performance on Hyper-V](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md).  

 The “\Hyper-V Hypervisor Logical Processor(_Total)\\% Total Run Time” Performance Monitor counter measures the overall resource utilization of all guest machines and the hypervisor on the Hyper-V host. If this value is above 90%, the server is running at maximum capacity; allocating additional virtual processors to virtual machines in this scenario can degrade overall system performance and should be avoided. For further details on using the HyperV performance counters, see the [Evaluating BizTalk Server Performance on Hyper-V](../technical-guides/evaluating-biztalk-server-performance-on-hyper-v.md) section of this guide.  


|                                                                      Operating system                                                                       | Virtual processor limit |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|
| [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. All editions of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] are 64-bit only. |            4            |
|                                               [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 64-bit                                               |            4            |
|                                               [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 32-bit                                               |            4            |
|                                                                      Windows 7 64-bit                                                                       |            4            |
|                                                                      Windows 7 32-bit                                                                       |            4            |
|                                                                    Windows Vista 64-bit                                                                     |            2            |
|                                                                    Windows Vista  32-bit                                                                    |            2            |

> [!NOTE]  
>  For more information about the guest operating systems that are supported on Hyper-V, see [http://go.microsoft.com/fwlink/?LinkID=118347](http://go.microsoft.com/fwlink/?LinkID=118347).  

##### Memory  
 The physical server requires enough memory for the root partition and any virtual machines running on the server. During testing, a minimum of 2GB of memory was allocated to the root partition and the **Memory/Available Mbytes** performance monitor counter was monitored to ensure no memory pressure was experienced.  

 The amount of memory that should be allocated to each virtual machine in a BizTalk Server environment depends on the workload and type of processing that will be performed. There are many factors that affect memory requirements of  BizTalk Server including:  

- Size of messages processed  

- Throughput of messages  

- Orchestration design  

- Pipeline processing  

- Number of BizTalk hosts that you plan to run within the virtual machine  

  For a comprehensive list of factors that affect memory, see “The Performance Factors” section of the BizTalk Server Performance Optimizations Guide at [http://go.microsoft.com/fwlink/?LinkId=122587](http://go.microsoft.com/fwlink/?LinkId=122587).  

  Proactively monitor the **Memory/Available Mbytes** counter from within each virtual machine and the root partition itself. The following guidelines from [Checklist: Measuring Performance on Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md) should be used to determine whether there is enough available physical memory for the virtual machine and for the root partition:  

- 50% of free memory available or more = Healthy  

- 25% of free memory available = Monitor  

- 10% of free memory available = Warning  

- Less than 5% of free memory available = Critical, performance will be adversely affected  

#### Choosing Root Operating System Version  
 Hyper-V is supported on a Server Core as well as a full installation of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. To minimize the overhead of the root partition, install Hyper-V on a Server Core installation of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. The Hyper-V role can be managed remotely from the Hyper-V Manager on a different system. Server Core provides a smaller disk and memory profile, therefore, leaving more resources available for virtual machines. For more information about the Server Core installation option available for [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], see [http://go.microsoft.com/fwlink/?LinkID=202439](http://go.microsoft.com/fwlink/?LinkID=202439).  

 If you choose to use a full installation of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], ensure that the root partition is dedicated only to the Hyper-V server role. Running additional server roles will consume memory, disk, processor, and network resources and will degrade performance.  

#### Creating Your Virtual Machines  
 After you have installed and configured the Hyper-V server role, you need to create the virtual machines. Before doing this, it is useful to answer the following questions:  

- What storage configuration will I use?  

- How many virtual processors does the guest operating system support?  

- How much memory will be allocated to the virtual machine?  

- How many virtual machines can I run on my Hyper-V Server?  

- How will I install the operating system onto the machine?  

  For more information about how to create and configure virtual machines, see [Create Virtual Machines](http://go.microsoft.com/fwlink/?LinkID=202440).  

##### Installing the Base Operating System  
 All the options available for a physical server installation are available in Hyper-V. A bootable CD/DVD-ROM media or an ISO image can be used to perform a manual installation. A network installation can be performed if the virtual machine has been configured with a network adapter connected to the same network as a server that hosts the ISO images.  

> [!IMPORTANT]  
>  Whichever installation method is chosen, for performance reasons it is critical the operating system integration components be installed for each virtual machine running under Hyper-V. The integration components provide a set of drivers and services that enable the guest machine to perform by using synthetic devices. Synthetic devices avoid the need for emulated devices, which are used on operating systems that do not support integration components. Emulated devices incur greater system overhead compared to synthetic devices.  

 To install and configure the machines used in this lab, an initial base image was created on a fixed size VHD. This involved a manual installation of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. Once all appropriate updates had been installed the base virtual machine was imaged using sysprep utility that is installed with Windows Server 2008, in the %WINDIR%\system32\sysprep directory.  

> [!NOTE]
>  Running Sysprep after BizTalk Server has been installed and configured on the server can be accomplished through the use of a Sysprep answer file and scripts provided with BizTalk Server. These sample scripts are designed for use with BizTalk Server installed on [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]. For more information see the BizTalk Server online documentation.  

## Installing and Configuring BizTalk Server  

- To minimize the time required to install virtual machines, create a base image consisting only of the guest operating system and software prerequisites. Use SysPrep to prepare the VHD image for reuse, and then base all your virtual machines (VMs) on this VHD.  

  > [!NOTE]
  >  With BizTalk Server, it is possible to run Sysprep against a base image *after*BizTalk Server has been installed and configured on the server. This can be accomplished through the use of a Sysprep answer file and scripts provided with BizTalk Server. These sample scripts are designed for use with BizTalk Server installed on   [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] . For more information see the BizTalk Server online documentation.  
  > 
  >  The Unattended Windows Setup Reference is available at [http://go.microsoft.com/fwlink/?LinkId=142364](http://go.microsoft.com/fwlink/?LinkId=142364).  

- Follow the recommendations in the “When Installing and Configuring BizTalk Server…” section of the topic [Checklist: Best Practices for Installing and Configuring BizTalk Server on Hyper-V](../technical-guides/checklist-best-practices-to-install-and-configure-biztalk-server-on-hyper-v.md).  

- For information on the supportability of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] in a Hyper-V environment, see [Appendix C: BizTalk Server and SQL Server Hyper-V Supportability](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md).
