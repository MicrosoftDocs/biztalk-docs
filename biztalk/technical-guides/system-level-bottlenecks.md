---
title: "System-Level Bottlenecks | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bdff435-76eb-495f-9fb6-1f1acef3921e
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# System-Level Bottlenecks
This topic describes how to address common system-level bottlenecks that can impact the performance of a BizTalk Server solution.

## Creating a snapshot of the baseline configuration
 Gathering the following information can provide you with a snapshot of the baseline configuration that you can use to assist in correcting system-level bottlenecks.

### Gather documentation
 Review the documentation of the architecture and infrastructure of your scenario.

### Run the Baseline Security Analyzer
 Follow these steps to run the Baseline Security Analyzer:

1.  Download the [Microsoft Baseline Security Analyzer 2.2](https://go.microsoft.com/fwlink/?LinKID=204006) (https://go.microsoft.com/fwlink/?LinkId=204006).

2.  Using a domain administrator account, log on to a computer on the same network that is hosting the BizTalk Server and SQL Server computers.

3.  Install the Microsoft Baseline Security Analyzer on the current computer (for example, one of the BizTalk Server computers or a separate computer).

4.  Execute a separate scan (**Start Scan**), specifying as a parameter the name or the IP address of each BizTalk Server and SQL Server computer.

5.  Copy each security report (.mbsa files) from the %userprofile%\SecurityScans directory.

### Run the BizTalk Server Best Practices Analyzer
 Follow these steps to run the BizTalk Server Best Practices Analyzer:

1.  Download the [BizTalk Server Best Practices Analyzer v1.2](https://go.microsoft.com/fwlink/?LinkID=83317) (https://go.microsoft.com/fwlink/?LinkID=83317).

2.  Using a user account that is part of the BizTalk Server Administrator security group, log on to a BizTalk Server node.

3.  Install the BizTalk Server Best Practices Analyzer on the current computer.

4.  Run the tool and save the report.

### Run MSInfo32 and save the results
 Follow these steps to run MSInfo32:

1.  Using a domain or a local administrator account, log on to each BizTalk Server and SQL Server computer.

2.  Launch a command prompt and change directories to the %windir%\system32 directory of the computer.

3.  Run MSinfo32.exe from the command prompt.

4.  Click the **File** menu and select the **Export** menu item to export to save the computer configuration.

### Export the BizTalk Server and SQL Server computer TCP/IP registry setting-
 Follow these steps to save the BizTalk Server and SQL Server TCP/IP registry settings:

1.  Launch a command prompt and change directories to the %windir%\system32 directory of the computer.

2.  Run Regedit.exe from the command prompt.

3.  Navigate to the following key in the registry:

    ```
    [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters] (network settings)
    ```

4.  Right-click this key and select **Export** to export the registry key to a file.

### Collect the BizTalk configuration files
 On each BizTalk Server node, collect the BizTalk Server configuration file, BTSNTSvc.exe.config file (or BTSNTSvc64.exe.config for 64-bit hosts), located in the BizTalk Server installation folder (e.g. C:\Program Files\Microsoft BizTalk Server 2010).

### Collect the .NET configuration files
 On each BizTalk Server node, collect the machine.config and web.config .NET Framework 4.0 configuration files. You can find the configuration files in the following location:

-   For 32-bit: %windir%\Microsoft.NET\Framework\v4.0.30319\CONFIG folder

-   For 64-bit: %windir%\Microsoft.NET\Framework64\v4.0.30319\CONFIG folder

### Use the BizTalk MsgBoxViewer tool to collect information about the MessageBox database
 Follow these steps to collect information about the MessageBox database using the BizTalk MsgBoxViewer tool:

1.  Download the [BizTalk MsgBoxViewer tool](https://go.microsoft.com/fwlink/?LinkID=117289) (https://go.microsoft.com/fwlink/?LinkID=117289).

2.  Log on to the BizTalk Server computer with a user account that is part of the BizTalk Server Administrator security group.

3.  Copy the MsgBoxViewer.exe to the BizTalk Server computer.

4.  Launch the tool.

5.  Click the **Optional Info to Collect** tab, and then click **Select All Info**.

6.  Click **Start to Collect**.

7.  When the Status label shows the **End Collection** message, switch to the folder containing the MsgBoxViewer.exe executable and copy the resulting report (.htm) and log files.

### Collect and store the source code for all components used in the solution
 Store the source code for all components (for example Orchestration, Custom Pipeline Component, and Helper components code) on a separate file share.

## Initial troubleshooting
 There are certain components of a BizTalk Server solution which, if not enabled, will cause performance problems regardless of the overall size or design of the BizTalk solution. The following preliminary troubleshooting tasks should be completed to rule out some of the “usual suspects” before engaging in an exhaustive bottleneck analysis of a BizTalk solution.

-   **Verify the Tracking host instance is running -** The Tracking host instance is responsible for moving both BAM and HAT data from the TrackingData table of the MessageBox database to the BizTalkDTADb and/or BAMPrimaryImport database tables. If the tracking host instance is not running, then tracking data will accumulate in the MessageBox database and negatively impact performance of the BizTalk Server solution.

-   **Verify the Enterprise Single Sign-On (ENTSSO) service is running on all BizTalk Server computers -** BizTalk host instances maintain a dependency on a locally running instance of the ENTSSO service. If the ENTSSO service is not running on the BizTalk Server, then host instances on the server will not be able to run either.

-   **Verify the SQL Server Agent service is running on all SQL Server computers -** The SQL Server Agent service must be running in order for the BizTalk SQL Server Agent jobs to execute. These jobs perform important functions to keep your servers operational and healthy.

-   **Verify the BizTalk SQL Server Agent jobs are enabled and running without exceptions -** Even if the SQL Server Agent service is running, it is imperative that all of the default BizTalk SQL Server Agent jobs are enabled and running successfully.

-   **Check the BizTalk Server and SQL Server event logs -** A cursory examination of the BizTalk Server or SQL Server event logs may reveal a problem that could otherwise take a significant amount of time to diagnose and resolve.

-   **Run the BizTalk Server Best Practices Analyzer -** The BizTalk Server Best Practices Analyzer examines a BizTalk Server deployment and generates a list of issues pertaining to best practices standards. The tool performs configuration-level verification by gathering data from different information sources, such as Windows Management Instrumentation (WMI) classes, SQL Server databases, and registry entries. The data is then used to evaluate the deployment configuration. The tool reads and reports only and does not modify any system settings, and is not a self-tuning tool. Download the BizTalk Server Best Practices Analyzer v1.2 from [BizTalk Server Best Practices Analyzer v1.2](https://go.microsoft.com/fwlink/?LinkID=83317) (https://go.microsoft.com/fwlink/?LinkID=83317).

## High-level system bottlenecks
 This section describes system-level bottlenecks that may be present in a BizTalk Server solution and possible mitigation strategies.

### Disk I/O bottlenecks
 Disk I/O refers to the number of read and write operations performed by your application on a physical disk or multiple disks installed in your server. Common activities that can cause disk I/O and related bottlenecks include long-running file I/O operations, data encryption and decryption, reading unnecessary data from database tables, and an insufficient physical memory, which can lead to excessive paging activity. Disk speed is another factor to consider when evaluating disk I/O bottlenecks; faster disks provide increased performance and help reduce disk I/O bottlenecks.

 The table below provides factors that should be considered when planning the disk subsystem for a BizTalk Server solution.

|Disk subsystem factor|Details|
|---------------------------|-------------|
|Disk memory cache and available physical memory|Because memory is cached to disk as physical memory becomes limited, make sure that you have a sufficient amount of memory available. When memory is scarce, more pages are written to disk, resulting in increased disk activity. Also, make sure to set the paging file to an appropriate size. Additional disk memory cache will help offset peaks in disk I/O requests. However, it should be noted that a large disk memory cache seldom solves the problem of not having enough spindles, and having enough spindles can negate the need for a large disk memory cache. For information on configuring the Windows paging file for optimal performance, see the section “Configure the Windows PAGEFILE for optimal performance” in the topic [Optimizing Operating System Performance](~/technical-guides/optimizing-operating-system-performance.md).|
|Storage controller type|If you have battery-backed cache, enable write caching to improve disk write performance on the transaction log file volumes and on the database volumes. Write caching provides a response time of 2 ms for a write I/O request, as opposed to a response time of 10 to 20 ms without write caching enabled. Enabling write caching greatly improves the responsiveness for client write requests. Read caching does not improve performance in a BizTalk Server scenario because it is only useful for sequential disk reads, which occur only in transaction log files.<br /><br /> Transaction log files are read from only when they are being played back, such as after a database restore or when a server is not properly shutdown. Larger caches allow for more data to be buffered, meaning that longer periods of saturation can be accommodated. If your controller allows you to configure the cache page size, you should set it to 4 KB. A larger size, such as 8 KB, results in wasted cache because a 4 KB I/O request takes up the entire cache page of 8 KB, thereby cutting your usable cache in half.|
|Spindles|Spindles are more important than capacity, and BizTalk Server performance is improved if the spindles support a high number of random I/O requests. Plan for no more than 80 percent total utilization to ensure sufficient I/O is available, even in cases of a spindle failure.|
|Raid|The RAID solution you use should be based on the cost and performance trade-offs that are appropriate for your environment. Therefore, more than one type of RAID solution may be recommended for a particular data storage requirement. General recommendations are as follows:<br /><br /> -   Use Raid-1+0 (striped sets in a mirrored set) for the BizTalk Server databases.<br />-   Use Raid-1 (mirrored set without parity) for the transaction log file volumes.<br />-   In general, Raid 5 (striped set with distributed parity) is not recommended as Raid 5 does not provide optimal reliability, availability and performance as compared to other Raid configurations.<br />-   Due to the possibility of permanent data loss, a Raid-0 (striped set without parity) configuration should never be used in a BizTalk Server production environment.|
|Bus type|Higher throughput provides better performance. In general, SCSI buses provide better throughput and scalability than IDE or ATA buses. You can use the following equation to determine the theoretical throughput limit for your bus type:<br /><br /> (Bus speed (in bits) / 8 bits per byte) X Operating speed (in MHz) = Throughput (in MB/s)<br /><br /> You can also improve disk I/O performance by placing multiple drives on separate I/O buses.|

#### Performance counters for measuring disk I/O bottlenecks

> [!NOTE]
>  When attempting to analyze disk performance bottlenecks, you should always use physical disk counters. However, if you use software RAID, you should use logical disk counters. As for Logical Disk and Physical Disk Counters, the same counters are available in each of these counter objects. Logical disk data is tracked by the volume manager (or managers), and physical disk data is tracked by the partition manager.

 The following performance counters should be used to determine if your system is experiencing a disk I/O related bottleneck:

-   **PhysicalDisk\Avg. Disk Queue Length**

    -   Threshold: Should not be higher than the number of spindles plus two.

    -   Significance: This counter indicates the average number of both read and writes requests that were queued for the selected disk during the sample interval. This counter is useful for gathering concurrency data, including data bursts and peak loads. These values represent the number of requests in flight below the driver taking the statistics. This means the requests are not necessarily queued but could actually be in service or completed and on the way back up the path. Possible in-flight locations include the following:

        -   SCSIport or Storport queue

        -   OEM driver queue

        -   Disk controller queue

        -   Hard disk queue

        -   Actively receiving from a hard disk

-   **PhysicalDisk\Avg. Disk Read Queue Length**

    -   Threshold: Should be less than two.

    -   Significance: This counter indicates the average number of read requests that were queued for the selected disk during the sample interval.

-   **PhysicalDisk\Avg. Disk Write Queue Length**

    -   Threshold: Should be less than two.

    -   Significance: This counter indicates the average number of write requests that were queued for the selected disk during the sample interval.

-   **PhysicalDisk\Avg. Disk sec/Read**

    -   Threshold: No specific value.

        -   Less than 10 milliseconds (ms) = good

        -   Between 15 and 25 ms = fair

        -   Greater than 25 ms = poor

    -   Significance: This counter indicates the average time, in seconds, of a data read operation from the disk. If the number is larger than 25 milliseconds (ms), that means the disk system is experiencing latency when reading from the disk. For mission-critical servers hosting BizTalk Server, the acceptable threshold is much lower, approximately 10 ms.

-   **PhysicalDisk\Avg. Disk sec/Write**

    -   Threshold: No specific value.

        -   Less than 10 milliseconds (ms) = good

        -   Between 15 and 25 ms = fair

        -   Greater than 25 ms = poor

    -   Significance: This counter indicates the average time, in seconds, of a data write operation to the disk. If the number is larger than 25 ms, the disk system experiences latency when writing to the disk. For mission-critical servers hosting BizTalk Server, the acceptable threshold is much lower, approximately 10 ms.

-   **PhysicalDisk\Avg. Disk sec/Transfer**

    -   Threshold: Should not be more than 18 milliseconds.

    -   Significance: This counter indicates the time, in seconds, of the average disk transfer. This may indicate a large amount of disk fragmentation, slow disks, or disk failures. Multiply the values of the **Physical Disk\Avg. Disk sec/Transfer** and **Memory\Pages/sec** counters. If the product of these counters exceeds 0.1, paging is taking more than 10 percent of disk access time, so you need more physical memory available.

-   **PhysicalDisk\Disk Writes/sec**

    -   Threshold: Depends on manufacturer’s specifications.

    -   Significance: This counter indicates the rate of write operations on the disk.

-   **Processor\\% DPC Time, % Interrupt Time and % Privileged Time -** If Interrupt Time and Deferred Procedure Call (DPC) time are a large portion of Privileged Time, the kernel is spending a significant amount of time processing I/O requests. In some cases performance can be improved by configuring interrupts and DPC affinity to a small number of CPUs on a multiprocessor system, which improves cache locality. In other cases, it works best to distribute the interrupts and DPCs among many CPUs, so as to keep the interrupt and DPC activity from becoming a bottleneck. For information on using the Interrupt Filter Configuration tool to bind network adapter interrupts to specific processors on multiprocessor computers, see the section “Use the Interrupt Filter Configuration tool to bind network adapter interrupts to specific processors on multiprocessor computers” in [Optimizing Operating System Performance](~/technical-guides/optimizing-operating-system-performance.md).

-   **Processor\DPCs Queued / sec -** Measures how DPCs are consuming CPU time and kernel resources.

-   **Processor\Interrupts / sec -** Another measurement of how interrupts are consuming CPU time and kernel resources. Modern disk controllers often combine or coalesce interrupts so that a single interrupt results in the processing of multiple I/O completions. Of course, there is a trade-off between delaying interrupts (and thus completions) and economizing CPU processing time.

#### Disk I/O tuning options
 If you determine that disk I/O is a bottleneck in your environment, the following techniques may be used to alleviate the bottleneck:

-   **Defragment your disks -** Use the available at [PageDefrag utility](https://go.microsoft.com/fwlink/?LinkId=108976) (https://go.microsoft.com/fwlink/?LinkId=108976) to defragment the Windows paging file and pre-allocate the Master File Tables.

-   **Use stripe sets to process I/O requests concurrently over multiple disks -** Use mirrored volumes to provide fault tolerance and increase I/O performance. If you do not require fault tolerance, implement stripe sets for fast reading and writing and improved storage capacity. When stripe sets are used, per disk utilization is reduced because work is distributed across the volumes, and overall throughput increases. If you adding additional disks in a stripe set does not increase throughput, then your system might be experiencing a bottleneck due to contention between disks by the disk controller. In this case, adding an additional disk controller will help distribute load and increase performance.

-   **Distribute workload among multiple drives -** Windows Clustering and Distributed File System provide solutions for load balancing on multiple disk drives.

-   **Limit the use of file compression or encryption -** File compression and encryption are I/O-intensive operations. You should only use them where absolutely necessary.

-   **Disable creation of short names -** If you are not supporting MS-DOS for Windows 3.x clients, disable short names to improve performance. For more information about disabling the creation of short names, see the section “Disable short-file-name (8.3) generation” in [Optimizing Operating System Performance](~/technical-guides/optimizing-operating-system-performance.md).

-   **Disable last access update -** By default, NTFS updates the date and time stamp of the last access on directories whenever it traverses the directory. For a large NTFS volume, this update process may hinder performance. For more information about disabling last access updates, see the section “Disable NTFS last access updates” in [Optimizing Operating System Performance](~/technical-guides/optimizing-operating-system-performance.md).

    > [!CAUTION]
    >  Some applications, such as incremental backup utilities, rely on the NTFS update information and will not function correctly without it.

-   **Reserve appropriate space for the master file table -** Add the **NtfsMftZoneReservation** entry to the registry depending on the number of files that are typically stored on your NTFS volumes. When you add this entry to the registry, the system reserves space on the volume for the master file table. Reserving space in this manner allows the master file table to grow optimally. If your NTFS volumes generally store relatively few files, set the value of this registry entry to the default value of 1. Typically you can use a value of 2 or 3 if your NTFS volumes store a moderate numbers of files, and use a value of 4 (the maximum) if your NTFS volumes tend to contain a relatively large number of files. However, make sure to test any settings greater than 2, because these greater values cause the system to reserve a much larger portion of the disk for the master file table. For more information about adding the **NtfsMftZoneReservation** to the registry, see the section “Increase space available for the master file table” in [Optimizing Operating System Performance](~/technical-guides/optimizing-operating-system-performance.md).

-   **Use the most efficient disk systems available -** In addition to the physical disk that is used, consider the type of disk controller and cabling that will be used. An efficient disk subsystem should also provide drivers that support interrupt moderation or interrupt avoidance to mitigate processor interrupt activity caused by disk I/O.

-   **Ensure that you are using the appropriate RAID configuration -** Use RAID 10 (striping and mirroring) for optimal performance and fault tolerance. The tradeoff is that using RAID 10 is expensive. Avoid using RAID 5 when you have extensive write operations. For more information about implementing RAID in a BizTalk Server environment, see the section “Disk Infrastructure” in the [BizTalk Server Database Optimization white paper](https://go.microsoft.com/fwlink/?LinkID=101578) (https://go.microsoft.com/fwlink/?LinkID=101578).

-   **Consider using database partitions -** If you have a database bottleneck, consider using database partitions and mapping disks to specific tables and transaction logs. The primary purpose of partitions is to overcome disk bottlenecks for large tables. If you have a table with large number of rows and you determine that it is the source of a bottleneck, consider using partitions. For SQL Server, you can use file groups to improve I/O performance. You can associate tables with file groups, and then associate the file groups with a specific hard disk. For more information about using optimizing filegroups for the BizTalk Server databases, see [Optimizing Filegroups for the Databases](~/technical-guides/optimizing-filegroups-for-the-databases2.md).

-   **Consider adding physical memory, if you have excessive page faults -** A high value for the **Memory: Pages/sec** performance counter could indicate excessive paging which will increase disk I/0. If this occurs, consider adding physical memory to reduce disk I/O and increase performance.

-   **Consider using a disk with a higher RPM rating or using a Storage Area Network (SAN) device -** Disks with higher RPM ratings offer improved performance compared to disks with lower RPM ratings. SAN devices typically offer top tier performance but at a price premium.

-   Follow the recommendations in [Optimizing Database Performance](~/technical-guides/optimizing-database-performance.md). This topic provides several recommendations for optimizing database performance both before and after configuring BizTalk Server.

### CPU bottlenecks
 Each application that runs on a server gets a time slice of the CPU. The CPU might be able to efficiently handle all of the processes running on the computer, or it might be overloaded. By examining processor activity and the activity of individual processes including thread creation, thread switching and context switching, you can gain insight into processor workload and performance.

#### You may have a CPU bottleneck if…

-   The value of the **Processor\\% Processor Time** performance counter often exceeds 75%.

-   The value of the **System\ Processor Queue Length** performance counter is 2 or more for a sustained period of time.

-   The value of the **Processor\\% Privileged Time** or **System\Context Switches/sec** performance counters are unusually high.

     If the value of **Processor\ % Processor Time** performance counter is high, then queuing occurs, and in most scenarios the value of **System\ Processor Queue Length** will also be high.

#### Performance counters for measuring CPU bottlenecks
 The following performance counters should be used to determine if your system is experiencing a CPU related bottleneck:

-   **Processor\\% Processor Time**

    -   Threshold: Should be less than 85%.

    -   Significance: This counter is the primary indicator of processor activity. High values many not necessarily be bad. However, if the other processor-related counters are increasing linearly such as **Processor\\% Privileged Time** or **System\Processor Queue Length**, high CPU utilization may be worth investigating.

-   **Processor\\% Privileged Time**

    -   Threshold: A figure that is consistently over 75 percent indicates a bottleneck.

    -   Significance: This counter indicates the percentage of time a thread runs in privileged mode. When your application calls operating system functions (for example to perform file or network I/O or to allocate memory), these operating system functions are executed in privileged mode.

-   **Processor\\% Interrupt Time**

    -   Threshold: Depends on the processor.

    -   Significance: This counter indicates the percentage of time the processor spends receiving and servicing hardware interrupts. This value is an indirect indicator of the activity of devices that generate interrupts, such as network adapters. A dramatic increase in this counter indicates potential hardware problems.

-   **System\Processor Queue Length**

    -   Threshold: An average value consistently higher than 2 indicates a bottleneck.

    -   Significance: If there are more tasks ready to run than there are processors, threads queue up. The processor queue is the collection of threads that are ready but not able to be executed by the processor because another thread is currently executing. A sustained or recurring queue of more than two threads is a clear indication of a processor bottleneck. You may get more throughput by reducing parallelism in those cases.

         You can use this counter in conjunction with the **Processor\\% Processor Time** counter to determine if your application can benefit from more CPUs. There is a single queue for processor time, even on multiprocessor computers. Therefore, in a multiprocessor computer, divide the Processor Queue Length (PQL) value by the number of processors servicing the workload.

         If the CPU is very busy (90 percent or higher utilization) and the PQL average is consistently higher than 2 per processor, you may have a processor bottleneck that could benefit from adding CPUs. Or, you could reduce the number of threads and queue more at the application level. This will cause less context switching, and less context switching is good for reducing CPU load. A common reason for a PQL value of 2 or higher with low CPU utilization is that requests for processor time arrive randomly and threads demand irregular amounts of time from the processor. This means that the processor is not a bottleneck but that the application threading logic should be improved.

-   **System\Context Switches/sec**

    -   Threshold: As a general rule, a context switching rate less than 5,000 per second per processor is not worth worrying about. If context switching rates exceed 15,000 per second per processor, then context switching can become a bottleneck.

    -   Significance: Context switching occurs when a higher priority thread preempts a lower priority thread that is currently running or when a high priority thread blocks other threads. High levels of context switching can occur when many threads share the same priority level. This often indicates that there are too many threads competing for the processors on the system. If both processor utilization and context switching levels are low, this is often an indication that threads are blocked.

#### Resolving CPU bottlenecks
 The first step is to identify which process is consuming excessive processor time. Use Windows **Task Manager** to identify which process is consuming high levels of CPU by looking at the **CPU** column on the **Processes** page. You can also determine this by monitoring **Process\\%Processor Time** in Performance Monitor and selecting the processes you want to monitor.

 Another powerful tool for determining which processes are consuming excessive CPU time is the Visual Studio Team System Profiler that is available with the Visual Studio Team System (VSTS) suite. For more information about using the Visual Studio Team System Profiler, see the Visual Studio Team System documentation.

 After you determine that your CPU is a bottleneck you have several options, including the following:

-   Add multiple processors if you have multi-threaded applications. Consider upgrading to a more powerful processor if your application is single-threaded.

-   If you observe a high rate of context switching, consider reducing the thread count for your process before increasing the number of processors.

-   Analyze and tune the application that is causing high CPU utilization. You can dump the running process by using the ADPLUS utility and analyze the cause by using Windbg. These utilities are part of the Windows debugging toolkit. You can download these tools from [Debugging Tools for Windows](https://go.microsoft.com/fwlink/?LinkID=106624) (https://go.microsoft.com/fwlink/?LinkID=106624).

-   Analyze the instrumentation log generated by your application to isolate the subsystem that is taking the maximum amount of time for execution. Determine whether a code review would be more beneficial than just tuning the BizTalk Server environment.

> [!NOTE]
>  Although you can change the process priority level of an application by using **Task Manager** or from a command prompt, you should generally avoid doing so.

### Memory bottlenecks
 When evaluating memory-related bottlenecks, consider unnecessary allocations, inefficient clean up, and inappropriate caching and state management mechanisms. To resolve memory-related bottlenecks, optimize your code to eliminate these issues and then tune the amount of memory allocated to your application(s). If you determine during tuning that memory contention and excessive paging are occurring, you may need to add additional physical memory to the server. Low memory leads to increased paging of an application's virtual address space to and from disk. If paging becomes excessive, disk I/O will increase and negatively impact overall system performance.

#### You might have a memory bottleneck if…

-   The value of the **Memory\Available MBytes** performance counter is low, either due to system memory limitations or an application that is not releasing memory. Monitor the value of the **Process\Working Set** performance counter for each process that is running. If value of the **Process\Working Set** remains high even when the process is not active, this may be an indication that the process is not releasing memory as it should.

-   The value of the **Memory\Pages/sec** performance counter is high. The average of **Memory\Pages Input/sec** divided by average of **Memory\Page Reads/sec** gives the number of pages per disk read. This value should not generally exceed five pages per second. A value greater than five pages per second indicates that the system is spending too much time paging and requires more memory (assuming that the application has been optimized).

#### Performance counters for measuring memory bottlenecks
 The following performance counters should be used to determine if your system is experiencing a memory related bottleneck:

-   **Memory\Available Mbytes**

    -   Threshold: A consistent value of less than 20 to 25 percent of installed RAM is an indication of insufficient memory.

    -   Significance: This indicates the amount of physical memory available to processes running on the computer. Note that this counter displays the last observed value only. It is not an average.

-   **Memory\Page Reads/sec**

    -   Threshold: Sustained values of more than five indicate a large number of page faults for read requests.

    -   Significance: This counter indicates that the working set of a process is too large for the available physical memory which is causing memory to page to disk. It shows the number of read operations, without regard to the number of pages retrieved in each operation. Higher values indicate a memory bottleneck.

         If a low rate of page-read operations coincides with high values for **Physical Disk\\% Disk Time** and **Physical Disk\Avg. Disk Queue Length**, a disk I/O bottleneck condition may exist. If an increase in queue length is not accompanied by a decrease in the pages-read rate, a memory bottleneck exists due to insufficient physical memory.

-   **Memory\Pages/sec**

    -   Threshold: A sustained value of more than five indicates a bottleneck.

    -   Significance: This counter indicates the rate at which pages are read from or written to disk to resolve hard page faults. Multiply the values of the **Physical Disk\Avg. Disk sec/Transfer** and **Memory\Pages/sec** performance counters. If the product of these values exceeds **0.1**, paging is utilizing more than 10 percent of disk access time, which indicates that insufficient physical memory is available.

-   **Memory\Pool Nonpaged Bytes**

    -   Threshold: Watch the value of **Memory\Pool Nonpaged Bytes** for an increase of 10 percent or more from its value at system startup.

    -   Significance: An increase of 10 percent or more from the value at startup may be an indication of a memory leak.

-   **Server\Pool Nonpaged Failures**

    -   Threshold: Regular nonzero values indicate a bottleneck.

    -   Significance: This counter indicates the number of times allocations from the non-paged pool have failed. The non-paged pool contains pages from a process's virtual address space that are not to be swapped out to the page file on disk, such as a process kernel object table. The availability of the non-paged pool determines how many processes, threads, and other such objects can be created. When allocations from the non-paged pool fail, this can be due to a memory leak in a process, particularly if processor usage has not increased accordingly.

-   **Server\Pool Paged Failures**

    -   Threshold: No specific value.

    -   Significance: This counter indicates the number of times allocations from the paged pool have failed. A positive value for this counter is an indication that the computer has insufficient physical memory or that the Windows paging file is too small.

-   **Server\Pool Nonpaged Peak**

    -   Threshold: No specific value.

    -   Significance: This is the maximum number of bytes in the non-paged pool that the server has reserved for use at any one point. It indicates how much physical memory the computer should have. Because the non-paged pool must be resident in physical memory and because there has to be some memory left over for other operations, as a rule of thumb the computer should have installed physical memory that is 4 times the value indicated for this counter.

-   **Memory\Cache Bytes**

    -   Threshold: No specific value.

    -   Significance: Monitors the size of cache under different load conditions. This value of this performance counter indicates the size of the static files cache. By default, this counter uses approximately 50 percent of available memory, but decreases if available memory shrinks, which affects system performance.

-   **Memory\Cache Faults/sec**

    -   Threshold: No specific value.

    -   Significance: This counter indicates how often the operating system looks for data in the file system cache but fails to find it. This value should be as low as possible.

-   **Cache\MDL Read Hits %**

    -   Threshold: The higher this value, the better the performance of the file system cache. Values should be as close to 100 percent as possible.

    -   Significance: This counter provides the percentage of Memory Descriptor List (MDL) Read requests to the file system cache, where the cache returns the object directly rather than requiring a read from the hard disk.

-   **Process\Working Set**

    -   Threshold: No specific value.

    -   Significance: The working set is the set of memory pages currently loaded in memory (physical + virtual). If the system has sufficient memory, it can maintain enough space in the working set so that it does not need to perform disk operations to page memory to disk. However, if there is insufficient memory, the system tries to reduce the working set by taking away the memory from the processes which results in an increase in page faults. When the rate of page faults rises, the system tries to increase the working set of the process. If you observe wide fluctuations in the working set, it might indicate a memory shortage. Higher values in the working set may also be due to multiple assemblies in an application. You can improve the working set by using assemblies shared in the global assembly cache.

#### Resolving memory bottlenecks
 If you determine that memory is a bottleneck in your BizTalk Server environment, use one or more of the following methods to resolve the bottleneck:

-   Tune the amount of memory allocated if you can control the allocation. For example, you can tune this for BizTalk Server, ASP.NET and SQL Server.

-   Increase the size of the Windows paging file and follow the steps in the “Configure the Windows PAGEFILE for optimal performance” section of [Optimizing Operating System Performance](~/technical-guides/optimizing-operating-system-performance.md).

-   Turn off services that are not used. Stopping services that you do not use regularly saves memory and improves system performance. For more information, see the “Disable non-essential services” section of [Optimizing Operating System Performance](~/technical-guides/optimizing-operating-system-performance.md).

-   Remove unnecessary protocols and drivers. Even idle protocols use space in the paged and non-paged memory pools. Drivers also consume memory, so you should remove unnecessary ones. For more information, see the “Remove unnecessary network protocols” section of [Optimizing Operating System Performance](~/technical-guides/optimizing-operating-system-performance.md).

-   Install additional physical memory on the computers in the BizTalk Server environment.

> [!NOTE]
>  On a 32-bit system, BizTalk can use a maximum of 2GB of memory, the limit increases to 3GB with BizTalk Server 2010 and later if the /3GB switch is used. For more information on memory usage, see [Memory Limits for Windows Releases](https://go.microsoft.com/fwlink/?LinkId=118349) (https://go.microsoft.com/fwlink/?LinkId=118349).

### Network I/O bottlenecks

#### You might have a network I/O bottleneck if…

-   The value of the **Network Interface\Bytes Total/sec** performance counter exceeds 80% of available network bandwidth.

-   The value of the **Server\Bytes Total/sec** performance counter is greater than 50% of available network bandwidth.

#### Performance counters for measuring network I/O bottlenecks
 The following performance counters should be used to measure network I/O and determine if your system is experiencing a network I/O related bottleneck:

-   **Network Interface\Bytes Total/sec**

    -   Threshold: Sustained value of more than 80 percent of network capacity.

    -   Significance: This counter indicates the rate at which bytes are sent and received over each network adapter. This counter helps determine if a network adapter is saturated and whether you should add one or more network adapters to increase available network bandwidth.

-   **Network Interface\Bytes Received/sec**

    -   Threshold: No specific value.

    -   Significance: This counter indicates the rate at which bytes are received over each network adapter. Use the value of this counter to calculate the rate of incoming data as a percentage of total available bandwidth. This will help determine if network bandwidth should be increased on the client sending data to BizTalk Server or if network bandwidth should be increased on the BizTalk Server computer itself.

-   **Network Interface\Bytes Sent/sec**

    -   Threshold: No specific value.

    -   Significance: This counter indicates the rate at which bytes are sent over each network adapter. Use the value of this counter to calculate the rate of outgoing data as a percentage of total available bandwidth. This will help determine if network bandwidth should be increased on the BizTalk Server sending data to a client or if network bandwidth should be increased on the client computer receiving data from BizTalk Server.

-   **Server\Bytes Total/sec**

    -   Threshold: Sustained value of more than 50 percent of network capacity.

    -   Significance: This counter indicates the number of bytes sent and received over the network. Higher values indicate a network I/O bottleneck. If the sum of **Bytes Total/sec** for all servers is roughly equal to the maximum transfer rate of your network, consider subnetting the network to improve performance. For more information about subnetting a network to improve performance, see the **Subnets** section of the [BizTalk Server Database Optimization white paper](https://go.microsoft.com/fwlink/?LinkID=101578) (https://go.microsoft.com/fwlink/?LinkID=101578).

#### Resolving network I/O bottlenecks
 If you determine that network I/O is a bottleneck in your environment, use one or more of the following methods to resolve the bottleneck:

-   Follow the recommendations in the “General guidelines for improving network performance” section of [Optimizing Network Performance](~/technical-guides/optimizing-network-performance.md).

-   Run the Windows Powershell network optimization script described in the topic [Optimizing Network Performance](~/technical-guides/optimizing-network-performance.md) on each computer in the BizTalk Server environment.

## See Also
 [Finding and Eliminating Bottlenecks](~/technical-guides/finding-and-eliminating-bottlenecks.md)