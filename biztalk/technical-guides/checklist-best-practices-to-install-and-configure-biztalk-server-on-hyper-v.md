---
description: "Learn more about: Checklist: Best Practices for Installing and Configuring BizTalk Server on Hyper-V"
title: "Checklist: Best Practices to install and configure on Hyper-V"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Checklist: Best Practices for Installing and Configuring BizTalk Server on Hyper-V
The sections below are a summary of the installation and configuration requirements described in the [Deploying BizTalk Server on Hyper-V](../technical-guides/deploying-biztalk-server-on-hyper-v.md) section of this guide. These should be used as a quick reference when installing, configuring and deploying [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a Hyper-V environment. Links to the relevant sections are provided for further information.

## Before Installing Hyper-V

- Hyper-V is a server role available for 64-bit editions of Windows Server. See [Checklist: Best Practices for Installing and Configuring BizTalk Server on Hyper-V](../technical-guides/checklist-best-practices-to-install-and-configure-biztalk-server-on-hyper-v.md)

- Ensure that your processor supports hardware-assisted virtualization and Data Execution Prevention (DEP) and that these features are enabled. This requires a processor that is compatible with Intel Virtualization Technology (Intel VT) or AMD Virtualization (AMD-V). See [Install the Hyper-V role](/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server).

- Use Windows Server Core Edition for the root partition. This will minimize server overhead and improve Hyper-V performance. See [Install Server Core](/windows-server/get-started/getting-started-with-server-core).

- Run only the Hyper-V server role on the root partition. See [Performance Tuning Hyper-V Servers](/windows-server/administration/performance-tuning/role/hyper-v-server/):

  **Dedicated Server Role**: The root partition should be dedicated to the virtualization server role. Additional server roles can adversely affect the performance of the virtualization server, especially if they consume significant CPU, memory, or I/O bandwidth. Minimizing the server roles in the root partition has additional benefits such as reducing the attack surface and the frequency of updates. System administrators should consider carefully what software is installed in the root partition because some software can adversely affect the overall performance of the virtualization server.

  See [Hyper-V Configuration](/windows-server/administration/performance-tuning/role/hyper-v-server/configuration) for guidance.

## When Creating Hyper-V Virtual Machines

- Using a fixed size virtual hard disk (VHD) provides improved performance compared to dynamically-resized VHDs for operating system drives. See [Hyper-V Storage I/O Performance](/windows-server/administration/performance-tuning/role/hyper-v-server/storage-io-performance) for guidance:

  **Fixed-size VHD**: Space for the VHD is first allocated when the VHD file is created. This type of VHD is less apt to fragment, which reduces the I/O throughput when a single I/O is split into multiple I/Os. It has the lowest CPU overhead of the three VHD types because reads and writes do not need to look up the mapping of the block.

- Use fixed-size virtual hard drive (VHD) disks for high disk I/O activities and configure disks for data volumes using the SCSI controller. For highly intensive storage I/O workloads that span multiple data drives, each VHD should be attached to a separate synthetic SCSI controller for better overall performance. In addition, each VHD should be stored on separate physical disks.

  See [Hyper-V Storage I/O Performance](/windows-server/administration/performance-tuning/role/hyper-v-server/storage-io-performance) for guidance:

  **Synthetic SCSI Controller**: The synthetic storage controller provides significantly better performance on storage I/Os with reduced CPU overhead than the emulated IDE device. The VM integration services include the enlightened driver for this storage device and are required for the guest operating system to detect it. The operating system disk must be mounted on the IDE device for the operating system to boot correctly, but the VM integration services load a filter driver that reroutes IDE device I/Os to the synthetic storage device.

  We strongly recommend that you mount the data drives directly to the synthetic SCSI controller because that configuration has reduced CPU overhead. You should also mount log files and the operating system paging file directly to the synthetic SCSI controller if their expected I/O rate is high.

  For highly intensive storage I/O workloads that span multiple data drives, each VHD should be attached to a separate synthetic SCSI controller for better overall performance. In addition, each VHD should be stored on separate physical disks.

- Use the SCSI controller to attach VHD disks for high I/O activities, such as for SQL Server data and log files. Do not attach a system disk to a SCSI controller. A virtual hard disk that contains an operating system must be attached to an IDE controller.

  Even though Hyper-V IDE controller and SCSI controller offer comparable performance, the SCSI controller can only be installed if Hyper-V integration services are installed. Therefore, use of the SCSI controller to attach passthrough disks will ensure that Hyper-V integration services are installed which in turn will ensure optimal disk I/O performance.

- Use the Network Adapter instead of the Legacy Network Adapter when configuring networking for a virtual machine. The legacy network adapter is designed for operating systems that do not support integration components.

  **Synthetic Network Adapter**: Hyper-V features a synthetic network adapter that is designed specifically for VMs to achieve significantly reduced CPU overhead on network I/O when it is compared to the emulated network adapter that mimics existing hardware. The synthetic network adapter communicates between the child and root partitions over VMBus by using shared memory for more efficient data transfer. The emulated network adapter should be removed through the VM settings dialog box and replaced with a synthetic network adapter. The guest requires that the VM integration services be installed.

- Ensure that integration services are installed on any enlightened guest operating systems and verify that the most current version of integration services is installed. To check for the most current version of integration services, run **Windows Update**.

  See [Hyper-V Processor Performance](/windows-server/administration/performance-tuning/role/hyper-v-server/processor-performance) for guidance:

  **Enlightened Guests**: It may be recommended that you use Windows Server as a guest operating system. The enlightenments decrease the CPU overhead of Windows that runs in a VM. The integration services provide additional enlightenments for I/O. Depending on the server load, it can be appropriate to host a server application in a Windows Server guest for better performance.

- Whenever possible, configure a 1-1 allocation of virtual processors to available logical processors. For more information about configuring a 1-to-1 allocation of virtual processors to available logical processors see the “Optimize Processor Performance” section in [Checklist: Optimizing Performance on Hyper-V](/biztalk/technical-guides/checklist-optimizing-performance-on-hyper-v).

- Convert or migrate virtual machines running on Microsoft Virtual PC, Microsoft Virtual Server, or VMWare ESX Server to run on Hyper-V.

  - Use System Center Virtual Machine Manager to convert or migrate virtual machines to run on Hyper-V.
  - If required, the process of converting virtual machines running on Microsoft Virtual PC or Microsoft Virtual Server can be performed manually. For more information, see [Virtual Machine Migration Guide: How To Migrate from Virtual Server to Hyper-V](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd296684(v=ws.10)).
  - The sample tool **VMC2Hyper-V** can also be used to migrate virtual machines running on Microsoft Virtual PC or Microsoft Virtual Server to Hyper-V.

## When Installing and Configuring BizTalk Server

When installing BizTalk Server in a virtual environment, the same practices should be followed as in a physical environment. The following resources should be utilized when installing and during configuration of BizTalk Server:

- For instructions on how to install BizTalk Server on the guest operating system, see the [BizTalk Server installation guides](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).

- Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Best Practices Analyzer (BPA) tool on the completed BizTalk Server installation. Download the [BizTalk Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=43382).

- The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are hosted on SQL Server. Run theSQL Server Best Practices Analyzer (BPA) tool on the SQL Server instance before configuring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. Download the [SQL Server Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=29302).

- The Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operations Guide provides Operational Readiness Checklists that can be used to ensure that all necessary prerequisite software has been installed. Checklists that provide [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] specific configuration information are provided for all the components required as part of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stack including the operating system, IIS, and SQL Server. In addition, guidance is provided about how to configure BizTalk Server for high availability.

  Read the [BizTalk Operations Guide](biztalk-server-2010-operations-guide.md). 

- Optimize the performance of your BizTalk Server installation. See [BizTalk Server Performance Optimization Guide](biztalk-server-2010-performance-optimization-guide.md) for guidance.

- Install and run the BizTalk Health Monitor to analyze and validate the configuration of the BizTalk Server MessageBox database. Download the [BizTalk Health Monitor](https://www.microsoft.com/download/details.aspx?id=43716).

- Verify that CPU is being properly allocated to guest operating systems running in Hyper-V. See **Measuring Processor Performance** at [Checklist: Measuring Performance on Hyper-V](/biztalk/technical-guides/checklist-measuring-performance-on-hyper-v).
