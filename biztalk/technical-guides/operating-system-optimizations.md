---
title: "Operating System Optimizations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af2e77d0-d69b-4ae4-b689-96831fc4deed
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operating System Optimizations
This topic provides recommendations for optimizing performance of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers used in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. These optimizations are applied after [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has been installed and configured.  
  
## General guidelines for improving operating system performance  
 The following recommendations can be used to increase operating system performance:  
  
### Install the latest BIOS, storage area network (SAN) drivers, network adapter firmware and network adapter drivers  
 Hardware manufacturers regularly release BIOS, firmware, and driver updates that can improve performance and availability for the associated hardware. Visit the hardware manufacturer’s Web site to download and apply updates for the following hardware components on each computer in the BizTalk Server environment:  
  
1.  BIOS updates  
  
2.  SAN drivers (if using a SAN)  
  
3.  NIC firmware  
  
4.  NIC drivers  
  
### Assign the MSDTC log file directory to a separate dedicated drive  
 In a BizTalk Server environment with multiple MessageBox databases on separate SQL Server computers, additional overhead associated with Microsoft Distributed Transaction Coordinator (MSDTC) is incurred. By default, the MSDTC log files are located in the %systemdrive%\windows\system32\msdtc directory of the computers running the DTC service. To mitigate the possibility that DTC logging could become a performance bottleneck, consider moving the MSDTC log file directory to a fast disk drive. To change the MSDTC log file directory follow these steps:  
  
1.  Click **Start**, click **Run**, and type **dcomcnfg** to launch the **Component Services** Management console.  
  
2.  Expand **Component Services**, expand **Computers**, right-click **My Computer**, and then click **Properties**.  
  
3.  In the **My Computer Properties** dialog box, click the **MSDTC** tab.  
  
4.  In the **Location** edit box under **Log Information**, type the path where you want the new log to be created (for example, G:\Logs\DTCLog).  
  
5.  Click **Reset log**, and you will be prompted for service restart. Click **OK** to restart the DTC service, and then click **OK** to confirm the MSDTC service has been restarted.  
  
### Configure antivirus software to avoid real-time scanning of BizTalk Server executables and file drops  
 Antivirus software real-time scanning of BizTalk Server executable files and any folders or file shares monitored by BizTalk Server receive locations can negatively impact BizTalk Server performance. If antivirus software is installed on the BizTalk Server computer(s), disable real-time scanning of non-executable file types referenced by any BizTalk Server receive locations (usually .XML, but can also be .csv, .txt, etc.) and configure antivirus software to exclude scanning of BizTalk Server executable Files  
  
### Disable intrusion detection network scanning between computers in the BizTalk Server environment  
 Intrusion detection software can slow down or even prevent valid communications over the network. If intrusion detection software is installed, disable network scanning between BizTalk Server computers and external data repositories (SQL Server) computers or messaging services (Message Queuing, WebSphere MQSeries, etc.) computers.  
  
### Defragment all disks in the BizTalk Server environment on a regular basis  
 Excessive disk fragmentation in the BizTalk Server environment will negatively impact performance. Follow these steps to defragment disks in the BizTalk Server environment:  
  
1.  Defragment all disks (local and SAN/NAS) on a regular basis by scheduling off-hours disk defragmentation.  
  
2.  Defragment the Windows PageFile and pre-allocate the Master File Tables of each disk in the BizTalk Server environment to boost overall system performance.  
  
    > [!NOTE]  
    >  Use the PageDefrag utility available at [http://go.microsoft.com/fwlink/?LinkId=108976](http://go.microsoft.com/fwlink/?LinkId=108976) to defragment the Windows PageFile and pre-allocate the Master File Tables.  
  
### If antivirus software is installed on the SQL Server computer(s), disable real-time scanning of data and transaction files  
 Real-time scanning of the SQL Server data and transaction files (.mdf, .ndf, .ldf, .mdb) can increase disk I/O contention and reduce SQL Server performance. Note that the names of the SQL Server data and transaction files may vary between BizTalk Server environments. For more information about the data and transaction files created with a default BizTalk Server configuration, see[Optimizing Filegroups for the Databases](http://msdn.microsoft.com/library/ee377060\(v=bts.70\).aspx).  
  
### Configure MSDTC for BizTalk Server  
 Review the following information to configure MSDTC for BizTalk Server:  
  
-   To configure MSDTC on the BizTalk Server, see “Enable DTC on the Local Host Server” section of the BizTalk Server 2010 installation guide at [http://go.microsoft.com/fwlink/?LinkID=191321](http://go.microsoft.com/fwlink/?LinkID=191321).  
  
-   "Troubleshooting Problems with MSDTC" at [http://go.microsoft.com/fwlink/?LinkID=202142](http://go.microsoft.com/fwlink/?LinkID=202142).  
  
### Configure firewall(s) for BizTalk Server  
  
> [!NOTE]  
>  This step is only required if one or more firewalls are in place in your BizTalk Server environment.  
  
 Review the following information to configure firewall(s) for BizTalk Server:  
  
-   "Required Ports for BizTalk Server" at [http://go.microsoft.com/fwlink/?LinkId=101607](http://go.microsoft.com/fwlink/?LinkId=101607).  
  
-   ”How to configure RPC dynamic port allocation to work with firewalls” at [http://go.microsoft.com/fwlink/?LinkID=76145](http://go.microsoft.com/fwlink/?LinkID=76145).  
  
### Use the NTFS file system on all volumes  
 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] offers multiple file system types for formatting drives, including NTFS, FAT, and FAT32. NTFS should always be the file system of choice for servers.[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]  
  
 NTFS offers considerable performance benefits over the FAT and FAT32 file systems and should be used exclusively on Windows servers. In addition, NTFS offers many security, scalability, stability and recoverability benefits over FAT and FAT32.  
  
 Under previous versions of Windows, FAT and FAT32 were often implemented for smaller volumes (say <500 MB) because they were often faster in such situations. With disk storage relatively inexpensive today and operating systems and applications pushing drive capacity to a maximum, it is unlikely that such small volumes will be in use. FAT32 scales better than FAT on larger volumes but is still not an appropriate file system for Windows servers.  
  
 FAT and FAT32 have often been implemented in the past as they were seen as more easily recoverable and manageable with native DOS tools in the event of a problem with a volume. Today, with the various NTFS recoverability tools built both natively into the operating system and available as third-party utilities available, there should no longer be a valid argument for not using NTFS for file systems.  
  
### Do not use NTFS file compression  
 Though using NTFS file system compression is an easy way to reduce space on volumes, it is not appropriate for enterprise file servers. Implementing compression places an unnecessary overhead on the CPU for all disk operations and is best avoided. Think about options for adding additional disks, near-line storage or consider archiving data before seriously considering file system compression.  
  
### Review disk controller stripe size and volume allocation units  
 When configuring drive arrays and logical drives within your hardware drive controller, ensure you match the controller stripe size with the allocation unit size that the volumes will be formatted with. This will ensure disk read and write performance is optimal and offer better overall server performance.  
  
 Configuring larger allocation unit (or cluster or block) sizes will cause disk space to be used less efficiently, but will also provide higher disk I/O performance as the disk head can read in more data during each read activity.  
  
 To determine the optimal setting to configure the controller and format the disks with, you should determine the average disk transfer size on the disk subsystem of a server with similar file system characteristics. Use the [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] Performance Monitor tool to monitor the Logical Disk object counters of Avg. Disk Bytes/Read and Avg. Disk Bytes/Write over a period of normal activity to help determine the best value to use.  
  
 Although smaller allocation unit sizes may be warranted if the system will be accessing many small files or records, an allocation unit size of 64 KB delivers sound performance and I/O throughput under most circumstances. Improvements in performance with tuned allocation unit sizes can be particularly noted when disk load increases.  
  
> [!NOTE]  
>  Either the FORMAT command line tool or the Disk Management tool is required to specify an allocation unit size larger than 4096 bytes (4 KB) when formatting volumes. Windows Explorer will only format up to this threshold. The CHKDSK command can be used to confirm the current allocation unit size of a volume however it needs to scan the entire volume before the desired information is displayed (shown as Bytes in each allocation unit).  
  
### Monitor drive space utilization  
 The less data on a disk, the faster it will operate. This is because on a well defragmented drive, data is written as close to the outer edge of the disk as possible because this is where the disk spins the fastest and yields the best performance.  
  
 Disk seek time is normally considerably longer than read or write activities. As noted above, data is initially written to the outside edge of a disk. As demand for disk storage increases and free space reduces, data is written closer to the center of the disk. Disk seek time is increased in locating the data as the head moves away from the edge, and when found, it takes longer to read, hindering disk I/O performance.  
  
 This means that monitoring disk space utilization is important not just for capacity reasons but for performance also.  
  
 As a rule of thumb, work towards a goal of keeping disk free space between 20% to 25% of total disk space. If free disk space drops below this threshold, then disk I/O performance will be negatively impacted.  
  
### Implement a strategy to avoid disk fragmentation  
 Run a defragmenter utility regularly on your disks, including the root drive, to prevent performance degradation. Do this weekly on busy disks. A disk defragmenter is installed with Windows Server and can be run from a Scheduled Task at specified intervals.  
  
### Optimize Windows Server performance for background services  
 The BizTalk Server process (BTSNTSVC.exe) runs as a background service. By default, [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] is configured to adjust for best performance of application programs and not for background services.  
  
 [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] uses preemptive multi-tasking to prioritize process threads that will be attended to by the CPU. Preemptive multi-tasking is a methodology whereby the execution of a process is halted and another process is started, at the discretion of the operating system. This scheme prevents a single thread from dominating the CPU.  
  
 Switching the CPU from executing one process to the next is known as context-switching. The Windows operating system includes a setting that determines how long individual threads are allowed to run on the CPU before a context-switch occurs and the next thread is serviced. This amount of time is referred to as a quantum. This setting lets you choose how processor quanta are shared between foreground programs and background services. Typically for a server it is not desirable to allow a foreground program to have more CPU time allocated to it than background services. That is, all applications and their processes running on the server should be given equal consideration for CPU time.  
  
 To increase performance for background service like BizTalk host instances, follow these steps:  
  
1.  Click **Start**, click **Control Panel**, and then click **System**.  
  
2.  Click the **Advanced** tab, and then click **Settings** under **Performance**.  
  
3.  Click the **Advanced** tab, click **Background services**, and then click **OK** twice.  
  
### Manually load Microsoft Certificate Revocation lists  
 When starting a .NET application, the .NET Framework will attempt to download the Certificate Revocation list (CRL) for any signed assembly. If your system does not have direct access to the Internet, or is restricted from accessing the Microsoft.com domain, this may delay startup of BizTalk Server. To avoid this delay at application startup, you can use the following steps to manually download and install the code signing Certificate Revocation Lists on your system.  
  
1. Download the latest CRL updates from [http://crl.microsoft.com/pki/crl/products/CodeSignPCA.crl](http://go.microsoft.com/fwlink/?LinkID=117794) and [http://crl.microsoft.com/pki/crl/products/CodeSignPCA2.crl](http://go.microsoft.com/fwlink/?LinkId=117795).  
  
2. Move the CodeSignPCA.crl and CodeSignPCA2.crl files to the isolated system.  
  
3. From a command prompt, enter the following command to use the certutil utility to update the local certificate store with the CRL downloaded in step 1:  
  
    certutil –addstore CA c:\CodeSignPCA.crl  
  
   The CRL files are updated regularly, so you should consider setting a reoccurring task of downloading and installing the CRL updates. To view the next update time, double-click the .crl file and view the value of the **Next Update** field.  
  
### Synchronize time on all servers  
 Many operations involving tickets, receipts and logging rely on the local system clock being accurate. This is especially true in a distributed environment, where time discrepancies between systems may cause logs to be out of sync or tickets issued by one system to be rejected by another as expired or not yet valid.  
  
 For more information on configuring a server to automatically synchronize time, see [http://go.microsoft.com/fwlink/?LinkId=99420](http://go.microsoft.com/fwlink/?LinkId=99420).  
  
### Configure the Windows PAGEFILE for optimal performance  
 Follow these guidelines to configure the Windows PAGEFILE (paging file) for optimal performance:  
  
1.  **Move the paging file to a physical volume separate from the physical drive that operating system is installed on to reduce disk contention and increase disk performance** - On BizTalk Server computers, the performance gain associated with moving the paging file will vary depending on the document processing load. On SQL Server computers, moving the paging file to a separate volume is considered a best practice in all scenarios due to the disk intensive nature of SQL Server.  
  
2.  **Isolate the paging file onto one or more dedicated physical drives that are configured as either RAID-0 (striping) or RAID-1 (mirroring) arrays, or on single disks without RAID** - By using a dedicated disk or drive array where PAGEFILE.SYS is the only file on the entire volume, the paging file will not become fragmented, which will also improve performance. As with most disk-arrays, performance of the array is improved as the number of physical disks in the array is increased. If the paging file is distributed between multiple volumes on multiple physical drives in a disk array, the paging file size should be the same size on each drive in the array. When configuring a disk array, it is also recommended to use physical drives that have the same capacity and speed. Note that redundancy is not normally required for the paging file.  
  
3.  **Do not configure the paging file on a RAID 5 array** - Configuration of the paging file on a RAID 5 array is not recommended because paging file activity is write intensive and RAID 5 arrays are better suited for read performance than write performance.  
  
4.  **If you do not have resources to move the paging file to a physical volume other than the operating system is installed on, configure the paging file to reside on the same logical volume as the operating system** - Configuring the paging file to reside on a another logical volume which is on the same physical disk as the operating system will increase disk seek time and reduce system performance as the disk drive platter heads will be continually moving between the volumes, alternately accessing the page file, operating system files, application files, and data files. Also, the operating system is typically installed on the first partition of a physical disk, which is usually the closest to the outside edge of the physical disk and where disk speed is and associated performance are optimal for the disk.  
  
    > [!IMPORTANT]  
    >  If you do remove the paging file from the boot partition, Windows cannot create a crash dump file (MEMORY.DMP) in which to write debugging information in the event that a kernel mode STOP error occurs. If you do require a crash dump file, then you will have no option but to leave a paging file of at least the size of physical memory + 1 MB on the boot partition.  
  
5.  **Manually set the size of the paging file** – Manually setting the size of the paging file typically provides better performance than allowing the server to size it automatically or having no paging file at all. Best-practice tuning is to set the initial (minimum) and maximum size settings for the paging file to the same value. This ensures that no processing resources are lost to the dynamic resizing of the paging file, which can be intensive. This is especially true given that this resizing activity typically occurs when the memory resources on the system are already becoming constrained. Setting the same minimum and maximum page file size value also ensures the paging area on a disk is one single, contiguous area, improving disk seek time.