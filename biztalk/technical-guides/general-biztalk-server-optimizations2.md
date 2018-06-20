---
title: "General BizTalk Server Optimizations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41b452e9-d94c-4bcb-8ef6-e9cea28fc0ab
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# General BizTalk Server Optimizations
The following recommendations can be used to increase [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance. The optimizations listed in this topic are applied after [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has been installed and configured.  
  
## Create multiple BizTalk Server hosts and separate host instances by functionality  
 Separate hosts should be created for sending, receiving, processing, and tracking functionality. Creating multiple BizTalk hosts provides flexibility when configuring the workload in your BizTalk group and is the primary means of distributing processing across the BizTalk Servers in a BizTalk group. Multiple hosts also allow you to stop one host without affecting other hosts. For example, you may want to stop sending messages to let them queue up in the Messagebox database, while still allowing the inbound receiving of messages to occur. Separating host instances by functionality also provides the following benefits:  
  
-   Each host instance has its own set of resources such as memory, handles, and threads in the .NET thread pool.  
  
-   Multiple BizTalk hosts will also reduce contention on the Messagebox database host queue tables because each host is assigned its own work queue tables in the Messagebox database.  
  
-   Throttling is implemented in BizTalk Server at the host-level. This allows you to set different throttling characteristics for each host.  
  
-   Security is implemented at the host-level; each host runs under a discrete Windows identity. This would allow you, for example, to give Host_A access to FileShare_B, while not allowing any of the other hosts to access the file share.  
  
> [!NOTE]  
>  While there are benefits to creating additional host instances, there are also potential drawbacks if too many host instances are created. Each host instance is a Windows service (BTSNTSvc.exe), which generates additional load against the MessageBox database and consumes computer resources (such as CPU, memory, threads).  
  
 For more information about modifying BizTalk Server Host properties, see "How to Modify Host Properties" in the BizTalk Server help at [http://go.microsoft.com/fwlink/?LinkId=101588](http://go.microsoft.com/fwlink/?LinkId=101588).  
  
## Configure a dedicated tracking host  
 BizTalk Server is optimized for throughput, so the main orchestration and messaging engines do not actually move messages directly to the BizTalk Tracking or BAM databases, as this would divert these engines from their primary job of executing business processes. Instead, BizTalk Server leaves the messages in the MessageBox database and marks them as requiring a move to the BizTalk Tracking database. A background process (the tracking host) then moves the messages to the BizTalk Tracking and BAM databases. Because tracking is a resource intensive operation, a separate host should be created that is dedicated to tracking, thereby minimizing the impact that tracking has on hosts dedicated to message processing.  
  
 Using a dedicated tracking host also allows you to stop other BizTalk hosts without interfering with BizTalk Server tracking. The movement of tracking data out of the Messagebox database is critical for a healthy BizTalk Server system. If the BizTalk Host responsible for moving tracking data in the BizTalk group is stopped, the Tracking Data Decode service will not run. The impact of this is as follows:  
  
- HAT tracking data will not be moved from the Messagebox database to the BizTalk Tracking database.  
  
- BAM tracking data will not be moved from the Messagebox database to the BAM Primary Import database.  
  
- Because data is not moved, it cannot be deleted from the Messagebox database.  
  
- When the Tracking Data Decode service is stopped, tracking interceptors will still fire and write tracking data to the Messagebox database. If the data is not moved, this will cause the Messagebox database to become bloated, which will impact performance over time. Even if custom properties are not tracked or BAM profiles are not set up, by default some data is tracked (such as pipeline receive / send events and orchestration events). If you do not want to run the Tracking Data Decode service, turn off all tracking so that no interceptors save data to the database. To disable global tracking, see "How to Turn Off Global Tracking" in the BizTalk Server help at [http://go.microsoft.com/fwlink/?LinkId=101589](http://go.microsoft.com/fwlink/?LinkId=101589). Use the BizTalk Server Administration console to selectively disable tracking events.  
  
  The tracking host should be run on at least two computers running BizTalk Server (for redundancy in case one fails). For optimal performance, you should have at least one tracking host instance per Messagebox database. The actual number of tracking host instances should be (N + 1), where N = the number of Messagebox databases. The "+ 1" is for redundancy, in case one of the computers hosting tracking fails.  
  
  A tracking host instance moves tracking data for specific Messagebox databases, but there will never be more than one tracking host instance moving data for a specific Messagebox database. For example, if you have three Messagebox databases, and only two tracking host instances, then one of the host instances needs to move data for two of the Messagebox databases. Adding a third tracking host instance distributes the tracking host work to another computer running BizTalk Server. In this scenario, adding a fourth tracking host instance would not distribute any more tracking host work, but would provide an extra tracking host instance for fault tolerance.  
  
  For more information about the BAM Event Bus service, see the following topics in the BizTalk Server help:  
  
- "Managing the BAM Event Bus Service" at [http://go.microsoft.com/fwlink/?LinkId=101590](http://go.microsoft.com/fwlink/?LinkId=101590).  
  
- "Creating Instances of the BAM Event Bus Service" at [http://go.microsoft.com/fwlink/?LinkId=101591](http://go.microsoft.com/fwlink/?LinkId=101591).  
  
## Manage ASP.NET thread usage or concurrently executing requests for Web applications that host orchestrations published as a Web or WCF Service  
 The number of worker and I/O threads (IIS 6.0 and IIS 7.0 in classic mode) or the number of concurrently executing requests (IIS 7.0 integrated mode) for an ASP.NET Web application that hosts an orchestration published as a Web service should be modified under the following conditions:  
  
-   CPU utilization is not a bottleneck on the hosting Web server.  
  
-   The value of the **ASP.NET Apps v2.0.50727\Request Wait Time** or **ASP.NET Apps v2.0.50727\Request Execution Time** performance counters is unusually high.  
  
-   An error similar to the following generated in the Application log of the computer that hosts the Web application:  
  
    ```  
    Event Type: Warning  
    Event Source: W3SVC Event Category: None  
    Event ID: 1013  
    Date: 6/4/2009  
    Time: 1:03:47 PM  
    User: N/A  
    Computer: <ComputerName>  
    Description: A process serving application pool 'DefaultAppPool' exceeded time limits during shut down. The process id was '<xxxx>'  
    ```  
  
### Manage ASP.NET thread usage for Web applications that host orchestrations on IIS 6.0 and on IIS 7.0 running in Classic mode  
 When the **autoConfig** value in the machine.config file of an IIS 6.0 server or IIS 7.0 server running in Classic mode is set to **true**, ASP.NET 2.0 manages the number of worker threads and I/O threads that are allocated to any associated IIS worker processes:  
  
```  
<processModel autoConfig="true" />  
```  
  
 To manually modify the number of worker and I/O threads for an ASP.NET 2.0 Web application, open the associated machine.config file, and then enter new values for the **maxWorkerThreads** and **maxIoThreads** parameters:  
  
```  
<!-- <processModel autoConfig="true" /> -->  
    <processModel maxWorkerThreads="200" maxIoThreads="200" />  
```  
  
> [!NOTE]  
>  These values are for guidance only; ensure you test changes to these parameters.  
  
 For more information about tuning parameters in the machine.config file for an ASP.NET 2.0 Web application, see Microsoft Knowledge Base article  [821268 “Contention, poor performance, and deadlocks when you make Web service requests from ASP.NET applications”](http://go.microsoft.com/fwlink/?LinkID=66483) (http://go.microsoft.com/fwlink/?LinkID=66483).  
  
### Manage the number of concurrently executing requests for Web applications that host orchestrations on IIS 7.0 running in Integrated mode  
 When ASP.NET 2.0 is hosted on IIS 7.0 in integrated mode, the use of threads is handled differently than on IIS 6.0 or on IIS 7.0 in classic mode. When ASP.NET 2.0 is hosted on IIS 7.0 in integrated mode, ASP.NET 2.0 restricts the number of concurrently executing **requests** rather than the number of **threads** concurrently executing requests. For synchronous scenarios this will indirectly limit the number of threads but for asynchronous scenarios the number of requests and threads will likely be very different. When running ASP.NET 2.0 on IIS 7.0 in integrated mode, the **maxWorkerThreads** and **maxIoThreads** parameters in the machine.config file are not used to govern the number of running threads. Instead, the number of concurrently executing requests can be changed from the default value of 12 per CPU by modifying the value specified for **maxConcurrentThreadsPerCPU**. The **maxConcurrentThreadsPerCPU** value can be specified either in the reqistry or in the config section of an aspnet.config file. Follow these steps to change the default value for **maxConcurrentThreadsPerCPU** to govern the number of concurrently executing requests:  
  
 **To set the maxConcurrentThreadsPerCPU value in the registry**  
  
> [!WARNING]  
>  Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system. Use Registry Editor at your own risk. For more information about how to back up, restore, and modify the registry, see the Microsoft Knowledge Base article "Description of the Microsoft Windows registry" at [http://go.microsoft.com/fwlink/?LinkId=62729](http://go.microsoft.com/fwlink/?LinkId=62729).  
  
> [!NOTE]  
>  This setting is global and cannot be changed for individual application pools or applications.  
  
1. Click **Start**, click **Run**, type **regedit.exe**, and then click **OK** to start Registry Editor.  
  
2. Navigate to **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0**  
  
3. Create the key by following these steps:  
  
   1.  On the **Edit** menu, click **New**, and then click **Key**.  
  
   2.  Type **maxConcurrentThreadsPerCPU**, and then press **ENTER**.  
  
   3.  Under the **maxConcurrentThreadsPerCPU** key, create a DWORD entry with the new value for maxConcurrentThreadsPerCPU.  
  
   4.  Close Registry Editor.  
  
   **To set the maxConcurrentThreadsPerCPU value for an application pool in the config section of an aspnet.config file**  
  
> [!NOTE]  
>  Microsoft .NET Framework 3.5 Service Pack 1 must be installed to accommodate setting the values below via configuration file. You can download Microsoft .NET Framework 3.5 Service Pack 1 from [http://go.microsoft.com/fwlink/?LinkID=136345](http://go.microsoft.com/fwlink/?LinkID=136345).  
  
-   Open the aspnet.config file for the application pool, and then enter new values for the **maxConcurrentRequestsPerCPU** and **requestQueueLimit** parameters:  
  
```  
<system.web>  
    <applicationPool maxConcurrentRequestsPerCPU="12" requestQueueLimit="5000"/>  
</system.web>  
```  
  
> [!NOTE]  
>  This value overrides the value specified for **maxConcurrentThreadsPerCPU** in the registry. The requestQueueLimit setting is the same as processModel/requestQueueLimit, except that the setting in the aspnet.config file will override the setting in the machine.config file.  
  
## Define CLR hosting thread values for BizTalk host instances  
 Because a Windows thread is the most basic executable unit available to a Windows process, it is important to allocate enough threads to the .NET thread pool associated with an instance of a BizTalk host to prevent thread starvation. When thread starvation occurs, there are not enough threads available to perform the requested work that negatively impacts performance. At the same time, care should be taken to prevent allocating more threads to the.NET thread pool associated with a host than is necessary. The allocation of too many threads to the .NET thread pool associated with a host may increase context switching. Context switching occurs when the Windows kernel switches from running one thread to a different thread, which incurs a performance cost. Excessive thread allocation can cause excessive context switching, which will negatively impact overall performance.  
  
 Modify the number of Windows threads available in the .NET thread pool associated with an instance of a BizTalk host by creating the appropriate CLR Hosting values in the registry of the BizTalk Server.  
  
> [!WARNING]  
>  Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system. Use Registry Editor at your own risk. For more information about how to back up, restore, and modify the registry, see the Microsoft Knowledge Base article "Description of the Microsoft Windows registry" at [http://go.microsoft.com/fwlink/?LinkId=62729](http://go.microsoft.com/fwlink/?LinkId=62729).  
  
> [!NOTE]  
>  **Worker threads** are used to handle queued work items and **I/O threads** are dedicated callback threads associated with an I/O completion port to handle a completed asynchronous I/O request.  
  
 **To modify the number of threads available in the .NET thread pool associated with each instance of a BizTalk host, follow these steps:**  
  
1. Stop the BizTalk host instance.  
  
2. Click **Start**, click **Run**, type **regedit.exe**, and then click **OK** to start Registry Editor.  
   Navigate to **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc$**<em>hostname</em>] where *hostname* is the name of the host associated with the host instance.  
  
   > [!NOTE]  
   >  If you have upgraded your BizTalk Server 2006 installation from BizTalk Server 2004, this registry key may be represented as **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc***guid*] where *guid* is a GUID unique to each instance of a BizTalk Server host.  
  
3. Locate the **CLR Hosting** key. If this key does not exist, then create the key by following these steps:  
  
   1.  On the **Edit** menu, click **New**, and then click **Key**.  
  
   2.  Type **CLR Hosting**, and then press **ENTER**.  
  
4. Under the **CLR Hosting** key, create the following DWORD entries with the indicated values.  
  
   |DWORD entry|Default value|Recommended value|  
   |-----------------|-------------------|-----------------------|  
   |MaxIOThreads|20|100|  
   |MaxWorkerThreads|25|100 **Important:**  Increasing this value beyond 100 can have an adverse effect on the performance of the SQL Server computer hosting the BizTalk Server MessageBox database. When this problem occurs, SQL Server may encounter a deadlock condition. It is recommended this parameter is not increased beyond a value of 100.|  
   |MinIOThreads|1|25|  
   |MinWorkerThreads|1|25|  
  
   > [!NOTE]  
   >  These recommended values will be sufficient for most scenarios but may need to be increased depending on how many adapter handlers or orchestrations are running in each host instance.  
  
   > [!NOTE]  
   >  These values are implicitly multiplied by the number of processors on the server. For example, setting the MaxWorkerThreads entry to a value of 100 would effectively set a value of 400 on a 4 CPU server.  
  
5. Close Registry Editor.  
  
6. Restart the BizTalk host instance.  
  
## Disable tracking for orchestrations, send ports, receive ports, and pipelines when tracking is not required  
 Tracking incurs performance overhead within BizTalk Server as data has to be written to the MessageBox database and then asynchronously moved to the BizTalk Tracking database. If tracking is not a business requirement, then disable tracking to reduce overhead and increase performance. For more information about configuring tracking, see “Configuring Tracking Using the BizTalk Server Administration Console” in the BizTalk Server help at [http://go.microsoft.com/fwlink/?LinkID=106742](http://go.microsoft.com/fwlink/?LinkID=106742).  
  
## Decrease the purging period for the DTA Purge and Archive job from 7 days to 2 days in high throughput scenarios  
 By default, the purging interval for tracking data in BizTalk Server is set to 7 days. In a high throughput scenario, this can result in an excessive build up of data in the Tracking database, which will eventually impact the performance of the MessageBox and in turn negatively impact message processing throughput.  
  
 In high throughput scenarios, reduce the hard and soft purging interval from the default of 7 days to 2 days. For more information about configuring the purging interval, see “How to Configure the DTA Purge and Archive Job” in the BizTalk Server help at [http://go.microsoft.com/fwlink/?LinkID=104908](http://go.microsoft.com/fwlink/?LinkID=104908).  
  
## Install the latest service packs  
 The latest service packs for both BizTalk Server and the .NET Framework should be installed, as these contain fixes that can correct performance issues you may encounter.  
  
## Do not cluster BizTalk hosts unless absolutely necessary  
 While [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] and subsequent versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] allow you to configure a BizTalk host as a cluster resource, you should only consider doing this if you need to provide high availability to a resource that cannot be hosted across multiple BizTalk computers. As an example, ports using the FTP adapter should only reside on one host instance, as the FTP protocol does not provide file locking, however, this introduces a single point of failure which would benefit from clustering. Hosts that contain adapters, such as file, SQL, HTTP or processing only hosts, can be internally load balanced across machines and do not benefit from clustering.  
  
## Performance optimizations in the BizTalk Server documentation  
 Apply the following recommendations from the BizTalk Server documentation as appropriate:  
  
-   “Troubleshooting MessageBox Latency Issues” at [http://go.microsoft.com/fwlink/?LinkId=114747](http://go.microsoft.com/fwlink/?LinkId=114747)  
  
-   “Identifying Performance Bottlenecks” at [http://go.microsoft.com/fwlink/?LinkID=104418](http://go.microsoft.com/fwlink/?LinkID=104418)  
  
-   “Avoiding DBNETLIB Exceptions” at [http://go.microsoft.com/fwlink/?LinkID=108787](http://go.microsoft.com/fwlink/?LinkID=108787)  
  
-   “Avoiding TCP/IP Port Exhaustion” at [http://go.microsoft.com/fwlink/?LinkID=101610](http://go.microsoft.com/fwlink/?LinkID=101610)  
  
-   “Setting the EPM Threadpool Size” at [http://go.microsoft.com/fwlink/?LinkId=114748](http://go.microsoft.com/fwlink/?LinkId=114748)