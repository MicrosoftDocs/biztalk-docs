---
title: "Appendix B: Hyper-V Architecture and Feature Overview | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87b6b9a0-a470-43f7-b076-36075477cc34
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix B: Hyper-V Architecture and Feature Overview
This topic provides an overview of Hyper-V architecture, describes advantages and disadvantages of Hyper-V.  
  
## Hyper-V Architecture  
  
 Hyper-V is a hypervisor-based virtualization platform and an enabling technology for one of Windows Server’s marquee features, Live Migration. With Hyper-V, Windows Server is capable of Quick Migration, which could move VMs between physical hosts with only a few seconds of down-time. With Live Migration, moves between physical targets happen in millisecond, which means migration operations become invisible to connected users. See [What's new in Hyper-V on Windows Server](https://docs.microsoft.com/windows-server/virtualization/hyper-v/what-s-new-in-hyper-v-on-windows).
  
 The hypervisor is the processor-specific virtualization platform that can host multiple virtual machines (VMs) that are isolated from each other but share the underlying hardware resources by virtualizing the processors, memory, and I/O devices.  
  
 Guest operating systems running in a Hyper-V virtual machine provide performance approaching the performance of an operating system running on physical hardware *if* the necessary virtual server client (VSC) drivers and services are installed on the guest operating system. Hyper-V virtual server client (VSC) code, also known as Hyper-V enlightened I/O, enables direct access to the Hyper-V “Virtual Machine Bus” and is available with the installation of Hyper-V integration services. Hyper-V Integration services that provide VSC drivers are also available for other client operating systems.  
  
 Hyper-V supports isolation in terms of a partition. A partition is a logical unit of isolation, supported by the hypervisor, in which operating systems execute. The Microsoft hypervisor must have at least one parent, or root, partition, running Windows Server. The virtualization stack runs in the parent partition and has direct access to the hardware devices. The root partition then creates the child partitions which host the guest operating systems. A root partition creates child partitions using the hypercall application programming interface (API).  
  
 Partitions do not have access to the physical processor, nor do they handle the processor interrupts. Instead, they have a virtual view of the processor and run in a virtual memory address region that is private to each guest partition. The hypervisor handles the interrupts to the processor, and redirects them to the respective partition. Hyper-V can also hardware accelerate the address translation between various guest virtual address spaces by using an Input Output Memory Management Unit (IOMMU) which operates independent of the memory management hardware used by the CPU. An IOMMU is used to remap physical memory addresses to the addresses that are used by the child partitions.  
  
 Child partitions also do not have direct access to other hardware resources and are presented a virtual view of the resources, as virtual devices (VDevs). Requests to the virtual devices are redirected either via the VMBus or the hypervisor to the devices in the parent partition, which handles the requests. The VMBus is a logical inter-partition communication channel. The parent partition hosts Virtualization Service Providers (VSPs) which communicate over the VMBus to handle device access requests from child partitions. Child partitions host Virtualization Service Consumers (VSCs) which redirect device requests to VSPs in the parent partition via the VMBus. This entire process is transparent to the guest operating system.  
  
 Virtual Devices can also take advantage of a Windows Server Virtualization feature, named Enlightened I/O, for storage, networking, graphics, and input subsystems. Enlightened I/O is a specialized virtualization-aware implementation of high level communication protocols (such as SCSI) that utilize the VMBus directly, bypassing any device emulation layer. This makes the communication more efficient but requires an enlightened guest that is hypervisor and VMBus aware. Hyper-V enlightened I/O and a hypervisor aware kernel is provided via installation of Hyper-V integration services. Integration components, which include virtual server client (VSC) drivers, are also available for other client operating systems. Hyper-V requires a processor that includes hardware assisted virtualization, such as is provided with Intel VT or AMD Virtualization (AMD-V) technology.  
  
 The following diagram provides a high-level overview of the architecture of a Hyper-V environment running on Windows Server.  
  
 ![Hyper&#45;V architecture overview](../technical-guides/media/eadd2a84-3936-4b48-a0e2-05b94882d848.gif "eadd2a84-3936-4b48-a0e2-05b94882d848")  

  
 Acronyms and terms used in the diagram above are described below:  
  
- **APIC** – Advanced Programmable Interrupt Controller. A device which allows priority levels to be assigned to its interrupt outputs.  
  
- **Child Partition** – Partition that hosts a guest operating system. All access to physical memory and devices by a child partition is provided via the Virtual Machine Bus (VMBus) or the hypervisor.  
  
- **Hypercall** – Interface for communication with the hypervisor. The hypercall interface accommodates access to the optimizations provided by the hypervisor.  
  
- **Hypervisor** – A layer of software that sits between the hardware and one or more operating systems. Its primary job is to provide isolated execution environments called partitions. The hypervisor controls and arbitrates access to the underlying hardware.  
  
- **IC** – Integration component. Component that allows child partitions to communication with other partitions and the hypervisor.  
  
- **I/O stack** – Input/output stack.  
  
- **MSR** – Memory Service Routine.  
  
- **Root Partition** – Manages machine-level functions such as device drivers, power management, and device hot addition/removal. The root (or parent) partition is the only partition that has direct access to physical memory and devices.  
  
- **VID** – Virtualization Infrastructure Driver. Provides partition management services, virtual processor management services, and memory management services for partitions.  
  
- **VMBus** – Channel-based communication mechanism used for inter-partition communication and device enumeration on systems with multiple active virtualized partitions. The VMBus is installed with Hyper-V Integration Services.  
  
- **VMMS** – Virtual Machine Management Service. Responsible for managing the state of all virtual machines in child partitions.  
  
- **VMWP** – Virtual Machine Worker Process. A user mode component of the virtualization stack. The worker process provides virtual machine management services from the Windows Server instance in the parent partition to the guest operating systems in the child partitions. The Virtual Machine Management Service spawns a separate worker process for each running virtual machine.  
  
- **VSC** – Virtualization Service Client. A synthetic device instance that resides in a child partition. VSCs utilize hardware resources that are provided by Virtualization Service Providers (VSPs) in the parent partition. They communicate with the corresponding VSPs in the parent partition over the VMBus to satisfy a child partitions device I/O requests.  
  
- **VSP** – Virtualization Service Provider. Resides in the root partition and provide synthetic device support to child partitions over the Virtual Machine Bus (VMBus).  
  
- **WinHv** – Windows Hypervisor Interface Library. WinHv is essentially a bridge between a partitioned operating system’s drivers and the hypervisor which allows drivers to call the hypervisor using standard Windows calling conventions  
  
- **WMI** – The Virtual Machine Management Service exposes a set of Windows Management Instrumentation (WMI)-based APIs for managing and controlling virtual machines.  
  
  Most of these terms are defined in the [Glossary](../technical-guides/glossary8.md).  
  
> [!NOTE]  
>  [Hyper-V Technology Overview](https://docs.microsoft.com/windows-server/virtualization/hyper-v/hyper-v-technology-overview) is a good resource. 
  
## Advantages
 The advantages of running enterprise-level solutions in a Hyper-V virtualized environment include the following:  
  
1. **Consolidation of hardware resources** - Multiple physical servers can be easily consolidated into comparatively fewer servers by implementing virtualization with Hyper-V. Consolidation accommodates full use of deployed hardware resources. Hyper-V in Windows Server can access up to 64 logical CPUs on host computers. This capability not only takes advantage of new multicore systems, it also means greater virtual machine consolidation ratios per physical host.  
  
2. **Ease of administration**:  
  
   -   Consolidation and centralization of resources simplifies administration.  
  
   -   Implementation of scale-up and scale out is accommodated with much greater ease.  
  
3. **Significant cost savings**:  
  
   -   Hardware costs are significantly reduced because multiple virtual machines can run on a single physical machine, therefore, a separate physical machine is not required for every computer.  
  
   -   Hyper-V licensing costs may be included with the license cost of Windows Server, and may also be purchased as a stand-alone product.
  
   -   Power requirements may be significantly reduced by consolidating existing applications onto a virtualized Hyper-V environment due to the reduced physical hardware “footprint” that is required.  
  
4. **Fault tolerance support through Hyper-V clustering** – Because Hyper-V is a cluster aware application, Windows Server provides native host clustering support for virtual machines created in a Hyper-V virtualized environment.  
  
5. **Ease of deployment and management**:  
  
   -   Consolidation of existing servers into fewer physical servers simplifies deployment.  
  
   -   A comprehensive Hyper-V management solution is available with System Center Virtual Machine Manager. [What's new in VMM in System Center](https://docs.microsoft.com/system-center/vmm/whats-new?view=sc-vmm-2016) provides some guidance.
  
6. **Key Hyper-V performance characteristics**:  
  
   -   **Improved hardware sharing architecture** - Hyper-V provides improved access and utilization of core resources, such as disk, networking, and video when running guest operating systems with a hypervisor-aware kernel and which are equipped with requisite virtual server client (VSC) code (known as Hyper-V enlightened I/O). Enlightenments are enhancements made to the operating system to help reduce the cost of certain operating system functions like memory management. Integration components, which include VSC drivers, are also available for other client operating systems.  
  
        Disk performance is critical for disk I/O intensive enterprise applications such as Microsoft BizTalk Server and in addition to Hyper-V enlightened I/O; Hyper-V provides “Passthrough” disk support which provides disk performance on par with physical disk performance. Note that “Passthrough” disk support provides improved performance at a small cost to convenience. “Passthrough” disks are essentially physical disks/LUNs that are attached to a virtual machine and do not support some of the functionality of virtual disks, such as Virtual Machine Snapshots.  
  
   -   **Processor hardware-assisted virtualization support** – Hyper-V takes full advantage of processor hardware assisted virtualization support that is available with recent processor technology.  
  
   -   **Multi-core (SMP) guest operating system support** – Hyper-V provides the ability to support up to four processors in a virtual machine environment, which allows applications to take full advantage of multi-threading functionality in a virtual machine.  
  
   -   **Both 32-bit and 64-bit guest operating system support** – Hyper-V provides broad support for simultaneously running different types of operating systems, including 32-bit and 64-bit systems across different server platforms, such as Windows, Linux®, and others.  
  
7. **Comprehensive product support** – Because Microsoft enterprise applications (such as Exchange Server and SQL Server) are fully tested running in Hyper-V, Microsoft provides code fix support for these applications when deployed and run in a Hyper-V environment.  
  
8. **Scalability** – Additional processing power, network bandwidth, and storage capacity can be accomplished quickly and easily by apportioning additional available resources from the host computer to the guest virtual machine(s). This may require that the host computer is upgraded or that the guest virtual machines are moved to a more capable host computer.  
  
   For more in depth information about the benefits of leveraging virtualization technology provided with Hyper-V, see the [Hyper-V Technology Overview](https://docs.microsoft.com/windows-server/virtualization/hyper-v/hyper-v-technology-overview). 
  
## Disadvantages
 Some disadvantages of running enterprise-level solutions in a Hyper-V virtualized environment may include:  
  
-   **Hardware requirements –** Due to the demands of server consolidation, Hyper-V virtual machines tend to consume more CPU and memory, and require greater disk I/O bandwidth than physical servers with comparable computing loads. Because the Hyper-V server role is only available for 64-bit and all editions of Windows Server are 64-bit only, the physical hardware must support hardware assisted virtualization. This means the processor must be compatible with Intel VT or AMD Virtualization (AMD-V) technology, the system BIOS must support Data Execution Prevention (DEP), and DEP must be enabled.  
  
-   **Software requirements –** While most Microsoft software is supported running on Hyper-V virtual machines, some Microsoft software is still in the process of being tested to ensure compatibility with a Hyper-V virtualized environment. For example, most Microsoft enterprise level applications either support running on Hyper-V or are in the process of being tested for support on Hyper-V. For more information on the supportability of BizTalk Server and SQL Server on Hyper-V, see [Appendix C: BizTalk Server and SQL Server Hyper-V Supportability](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md).