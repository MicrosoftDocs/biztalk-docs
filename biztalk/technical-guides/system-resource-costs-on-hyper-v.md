---
title: "System Resource Costs on Hyper-V | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f25a76c-1c41-41c0-b28d-d7473dbe1cd1
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# System Resource Costs on Hyper-V
## System Resource Costs Associated with Running a Guest Operating System on Hyper-V  
 As with any server virtualization software, there is a certain amount of overhead associated with running the virtualization code required to support guest operating systems running on Hyper-V. The following list summarizes the overhead associated with specific resources when running guest operating systems on Hyper-V virtual machines:  
  
### CPU Overhead  
 The CPU overhead associated with running a guest operating system in a Hyper-V virtual machine was found to range between 9 and 12%.  For example, a guest operating system running on a Hyper-V virtual machine typically had available 88-91% of the CPU resources available to an equivalent operating system running on physical hardware.  
  
### Memory Overhead  
 For the Hyper-V host computer, the memory cost associated with running a guest operating system on a Hyper-V virtual machine was observed to be approximately 300 MB for the hypervisor, plus 32 MB for the first GB of RAM allocated to each virtual machine, plus another 8 MB for every additional GB of RAM allocated to each virtual machine. For more information about allocating memory to guest operating systems running on a Hyper-V virtual machine, see the “Optimizing Memory Performance” section in [Checklist: Optimizing Performance on Hyper-V](~/technical-guides/checklist-optimizing-performance-on-hyper-v.md).  
  
### Network Overhead  
 Network latency directly attributable to running a guest operating system in a Hyper-V virtual machine was observed to be less than 1 ms and the guest operating system typically maintained a network output queue length of less than one. For more information about measuring the network output queue length, see the “Measuring Network Performance” section in [Checklist: Measuring Performance on Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).  
  
### Disk Overhead  
 When using the passthrough disk feature in Hyper-V, disk I/O overhead associated with running a guest operating system in a Hyper-V virtual machine was found to range between 6 and 8 %. For example, a guest operating system running on Hyper-V typically had available 92-94% of the disk I/O available to an equivalent operating system running on physical hardware as measured by the open source disk performance benchmarking tool IOMeter.  
  
 For information about measuring disk latency on a Hyper-V host or guest operating system using Performance Monitor, see the “Measuring Disk I/O Performance” section in [Checklist: Measuring Performance on Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).  
  
 The remainder of this section provides background information on BizTalk Server disk performance, describes the test configuration parameters used, and provides a summary of test results obtained.  
  
#### Disk Performance When Running a BizTalk Server Solution on Hyper-V  
 BizTalk Server is an extremely database intensive application that may require the creation of up to 13 databases in SQL Server. BizTalk Server persists data to disk with great frequency and furthermore, does so within the context of an MSDTC transaction. Therefore, database performance is paramount to the overall performance of any BizTalk Server solution. Hyper-V provides a synthetic SCSI controller and an IDE filter driver which both provide significant performance benefits over using an emulated IDE device such as is provided with Virtual Server 2005.  
  
 Configure disks for data volumes using the SCSI controller. This will guarantee that the integration services are installed because the SCSI controller can only be installed if Hyper-V integration services are installed whereas the emulated IDE controller is available without installing Hyper-V integration services. Disk I/O performed using either the SCSI controller or the IDE filter driver provided with integration services is significantly better than disk I/O performance provided with the emulated IDE controller. Therefore, to ensure optimal disk I/O performance for the data files in a Hyper-V virtualized environment, install integration services on both the host and guest operating system and configure disks for data volumes with the synthetic SCSI controller. For highly intensive storage I/O workloads that span multiple data drives, each VHD should be attached to a separate synthetic SCSI controller for better overall performance. In addition, each VHD should be stored on separate physical disks or LUNs.  
  
#### Measuring PassThrough Disk Performance  
 During any consolidation exercise it is important to make maximum use of available resources. As discussed previously, storage I/O on SQL data volumes plays a significant part in the overall performance of a BizTalk Server solution. Therefore as part of this guidance, the relative performance of a physical disk to the performance of a passthrough disk in Hyper-V was tested. The relative performance of the MessageBox data drive in Physical_SQL01 and Virtual_SQL01 was measured using the IOMeter open source tool originally developed by Intel Corporation and now maintained by the open Source Development Lab (OSDL). For more information about IOMeter, see [http://go.microsoft.com/fwlink/?LinkId=122412](http://go.microsoft.com/fwlink/?LinkId=122412).  
  
 The following tables describe the physical and virtual hardware configuration used in the test environment, the IOMeter configuration options that were used, a description of the test that was run, and a summary of results.  
  
#### Configuration Used for Testing  
  
### Physical_SQL01  
  
|||  
|-|-|  
|**Model**|HP DL580|  
|**Processor**|Quad processor, Quad-core Intel Xeon 2.4Ghz|  
|**Memory**|8 GB|  
|**Networking**|HP NC3T3i Multifunction Gigabit Server adapter|  
|**SAN configuration**|Direct attached SAN storage (see table below)|  
  
### Physical_SQL01 – SAN Configuration  
  
|Drive letter|Description|LUN Size|RAID configuration|  
|------------------|-----------------|--------------|------------------------|  
|G:|Data_Sys|10|RAID 0 + 1|  
|H:|Logs_Sys|10|RAID 0 + 1|  
|I:|Data_TempDb|50|RAID 0 + 1|  
|J:|Logs_TempDb|50|RAID 0 + 1|  
|K:|Data_BtsMsgBox|300|RAID 0 + 1|  
|L:|Logs_BtsMsgBox|100|RAID 0 + 1|  
|M:|MSDTC|5|RAID 0 + 1|  
  
### Hyper-V_Host_SQL01  
  
|||  
|-|-|  
|**Model**|HP DL580|  
|**Processor**|Quad processor, Quad-core Intel Xeon 2.4Ghz|  
|**Memory**|32 GB|  
|**Networking**|Broadcom BCM5708C NetXtreme II GigEHP DL380 G5|  
  
### Virtual_SQL01 - Virtual Machine Configuration  
  
|||  
|-|-|  
|**Virtual processors**|4 allocated|  
|**Memory**|8 GB|  
|**Networking**|Virtual Machine Networking connected to:<br />Broadcom BCM5708C NetXtreme II GigE|  
|**Hard disk configuration**|**IDE controller** – 30 GB fixed vhd for Operating System<br />**SCSI controller** - 7 directly attached passthrough SAN LUNs (see table below)|  
  
### Virtual_SQL01 – SAN Configuration  
  
|Drive letter|Description|LUN Size|RAID configuration|  
|------------------|-----------------|--------------|------------------------|  
|G:|Data_Sys|10|RAID 0 + 1|  
|H:|Logs_Sys|10|RAID 0 + 1|  
|I:|Data_TempDb|50|RAID 0 + 1|  
|J:|Logs_TempDb|50|RAID 0 + 1|  
|K:|Data_BtsMsgBox|300|RAID 0 + 1|  
|L:|Logs_BtsMsgBox|100|RAID 0 + 1|  
|M:|MSDTC|5|RAID 0 + 1|  
  
#### IOMeter Configuration  
 The IOMeter tool can be used as a benchmark and troubleshooting tool by replicating the read/write performance of applications. IOMeter is a configurable tool that can be used to simulate many different types of performance. For purposes of this test scenario, IOMeter configuration parameters were set as described in the table below on both the physical [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer that was tested and on the guest operating system that was running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] in a Hyper-V virtual machine:  
  
### IOMeter – Passthrough Disk Comparison Test Configuration  
  
|                             |                     |
|-----------------------------|---------------------|
|       **Test length**       |     10 minutes      |
|      **Ramp up time**       |     30 seconds      |
|    **Number of workers**    |          4          |
|  **Transfer request size**  |        2 KB         |
| **Read/write distribution** | 66% read, 33% write |
|      **Burst length**       |       1 I/Os        |
|      **Target Drive**       |         K:\         |
  
#### Test Description  
 The [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] service was stopped on both servers to ensure that IOMeter was the only process performing I/O against the disk. The LUN’s used in this test were both located on the same SAN which was dedicated to this lab environment. No other I/O activity was performed against the SAN during the test to ensure that the results were not skewed. The test was then run by executing the IOMeter tool locally from each [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and the following performance monitor counters were collected:  
  
 **Collected from both Virtual_SQL01 and Physical_SQL01**:  
  
- \LogicalDisk(*)\\\*  
  
- \PhysicalDisk(*)\\\*  
  
  **Collected from virtual machine Hyper-V_02**:  
  
- \Hyper-V Virtual Storage Device\\*  
  
### Results  
 The passthrough disk was able to attain over 90% of the throughput of the SAN LUN connected directly to Physical_SQL01.  Total, read and write I/Os per second were all within 10% as was the total MB transferred per second.  Response times for healthy disks should be between 1-15 ms for read and write. Average I/O response times were less than 4 ms on both disks. Random reads response time was 5.4 ms on the physical and 5.7 ms on the pass-through disk. Write response time was less than 0.5 ms on both the physical and virtual environments.  
  
 The results indicate that a passthrough disk using the enlightened SCSI controller can provide over 90% of the performance of a directly connected physical disk. I/O subsystem performance is critical for efficient BizTalk Server operation, by providing excellent throughput and response times Hyper-V is an excellent candidate for consolidating a BizTalk Server environment. The table below provides a summary of the disk test results observed when comparing performance of a passthrough disk to a physical disk:  
  
|Measurement|Physical_SQL01 (Physical Disk)|Virtual_SQL01 (passthrough)|Relative performance of passthrough disks to physical disks|  
|-----------------|---------------------------------------|------------------------------------|-----------------------------------------------------------------|  
|Total I/Os per second|269.73|250.47|92.86%|  
|Read I/Os per second|180.73|167.60|92.74%|  
|Write I/Os per second|89.00|82.87|93.11%|  
|Total MBs per second|0.53|0.49|92.45%|  
|Average read response time (ms)|5.4066|5.7797|93.54%|  
|Average write response time (ms)|0.2544|0.3716|68.42% **Note:**  Although the relative performance of the pass through disks for Average write response time was 68.42% of the performance of physical disks, the Average write response time of the passthrough disks was still well within established acceptable limits of 10 ms.|  
|Average I/O response time (ms)|3.7066|3.9904|93.89%|  
  
> [!NOTE]  
>  The percentage values for Total I/Os per second, Read I/Os per second, Write I/Os per second, and Total MBs per second were calculated by dividing passthrough disk values by the corresponding physical disk values.  
>   
>  The percentage values for Average read response time (ms), Average write response time (ms), and Average I/O response time (ms) were calculated by dividing physical disk values by the corresponding passthrough disk values.