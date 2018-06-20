---
title: "General BizTalk Server Optimizations1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8032553-bae3-440d-9197-b926160b0bdf
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# General BizTalk Server Optimizations
The following recommendations can be used to increase BizTalk Server performance. The optimizations listed in this topic are applied after BizTalk Server has been installed and configured.  
  
## Configure MSDTC  
 To facilitate transactions between SQL Server and BizTalk Server, you must enable Microsoft Distributed Transaction Coordinator (MS DTC). To configure MSDTC on BizTalk Server, see the topic [General Guidelines for Improving Operating System Performance](../technical-guides/general-guidelines-for-improving-operating-system-performance.md).  
  
## Recommendations for configuring BizTalk Server hosts  
 This section provides recommendations for configuring BizTalk Server hosts.  
  
### Create multiple BizTalk Server hosts and separate host instances by functionality  
 Follow these guidelines to create multiple BizTalk Server hosts and allocate workload across those hosts:  
  
-   Create separate hosts for sending, receiving, processing, and tracking functionality. Creating multiple BizTalk hosts provides flexibility when configuring the workload in your BizTalk group and is the primary means of distributing processing across the computers running BizTalk Server in a BizTalk group. Using multiple hosts allows you to stop one host without affecting other hosts. For example, you may want to stop sending messages to let them queue up in the MessageBox database while still allowing a receive adapter running in a different host instance to receive inbound messages. Separating host instances by functionality also provides the following benefits:  
  
    -   Running multiple BizTalk hosts reduces contention on the MessageBox database host queue tables because each host is assigned its own work queue tables in the MessageBox database.  
  
    -   Throttling is implemented in BizTalk Server at the host-level. This allows you to set different throttling characteristics for each host.  
  
    -   Security is implemented at the host-level; each host runs under a discrete Windows identity. This allows you to, for example, give Host_A access to FileShare_B, while not allowing any of the other hosts to access the file share.  
  
-   Each host instance has its own set of resources such as memory, handles, and threads in the .NET thread pool. When allocating workload across hosts consider placing resources that scale together in the same host.  
  
-   Separate adapters and orchestrations that have different priorities for resources in different hosts. This technique accommodates the placement of hosts running high-priority applications on dedicated BizTalk Server computers.  
  
> [!NOTE]  
>  While there are benefits to creating additional host instances, there are also potential drawbacks if too many host instances are created. Each host instance is a Windows service (BTSNTSvc.exe), which generates additional load against the MessageBox database and consumes computer resources (such as CPU, memory, threads).  
  
 For more information about modifying BizTalk Server host properties, see [How to Modify Host Properties](http://go.microsoft.com/fwlink/?LinkID=154359) (http://go.microsoft.com/fwlink/?LinkID=154359) in the BizTalk Server 2010 Help.  
  
### Configure a dedicated tracking host  
 BizTalk Server is optimized for throughput, so the main orchestration and messaging engines do not actually move messages directly to the BizTalk Tracking or BAM databases, as this would divert these engines from their primary job of executing business processes. Instead, BizTalk Server leaves the messages in the MessageBox database and marks them as requiring a move to the BizTalk Tracking database. A background process (the tracking host) then moves the messages to the BizTalk Tracking and BAM databases. Because tracking is a resource-intensive operation, a separate host should be created that is dedicated to tracking, thereby minimizing the impact that tracking has on hosts dedicated to message processing. For optimal performance, there should be least one tracking host instance per MessageBox database. The actual number of tracking host instances should be N + 1, where N = the number of MessageBox databases. The "+ 1" is for redundancy, in case one of the computers hosting tracking fails.  
  
 Using a dedicated tracking host also allows you to stop other BizTalk hosts without interfering with BizTalk Server tracking. The movement of tracking data out of the MessageBox database is critical for a healthy BizTalk Server system. If the BizTalk Host responsible for moving tracking data in the BizTalk group is stopped, the Tracking Data Decode service will not run. The impact of this is as follows:  
  
- HAT tracking data will not be moved from the MessageBox database to the BizTalk Tracking database.  
  
- BAM tracking data will not be moved from the MessageBox database to the BAM Primary Import database.  
  
- Because data is not moved, it cannot be deleted from the MessageBox database.  
  
- When the Tracking Data Decode service is stopped, tracking interceptors will still fire and write tracking data to the MessageBox database. If the data is not moved, this will cause the MessageBox database to become bloated, which will impact performance over time. Even if custom properties are not tracked or BAM profiles are not set up, by default some data is tracked (such as pipeline receive / send events and orchestration events). If you do not want to run the Tracking Data Decode service, turn off all tracking so that no interceptors save data to the database. To disable global tracking, see [How to Turn Off Global Tracking](http://go.microsoft.com/fwlink/?LinkID=154193) (http://go.microsoft.com/fwlink/?LinkID=154193) in BizTalk Server 2010 Help. Use the BizTalk Server Administration console to selectively disable tracking events.  
  
  The tracking host should be run on at least two computers running BizTalk Server (for redundancy in case one fails). For optimal performance, you should have at least one tracking host instance per MessageBox database. The actual number of tracking host instances should be (N + 1), where N = the number of MessageBox databases. The "+ 1" is for redundancy, in case one of the computers hosting tracking fails.  
  
  A tracking host instance moves tracking data for specific MessageBox databases, but there will never be more than one tracking host instance moving data for a specific MessageBox database. For example, if you have three MessageBox databases, and only two tracking host instances, then one of the host instances needs to move data for two of the MessageBox databases. Adding a third tracking host instance distributes the tracking host work to another computer running BizTalk Server. In this scenario, adding a fourth tracking host instance would not distribute any more tracking host work, but would provide an extra tracking host instance for fault tolerance.  
  
  For more information about the BAM Event Bus service, see the following topics in BizTalk Server 2010 Help:  
  
- [Managing the BAM Event Bus Service](http://go.microsoft.com/fwlink/?LinkID=154194) (http://go.microsoft.com/fwlink/?LinkID=154194).  
  
- [Creating Instances of the BAM Event Bus Service](http://go.microsoft.com/fwlink/?LinkID=154195) (http://go.microsoft.com/fwlink/?LinkID=154195).  
  
### Do not cluster BizTalk hosts unless absolutely necessary  
 While BizTalk Server 2010 allows you to configure a BizTalk host as a cluster resource, you should only consider doing this if you need to provide high availability to a resource that cannot be hosted across multiple BizTalk computers. As an example, ports using the FTP adapter should only reside on one host instance, as the FTP protocol does not provide file locking. However, this introduces a single point of failure, which would benefit from clustering. Hosts that contain adapters, such as file, SQL, HTTP or processing only hosts, can be internally load balanced across computers, and do not benefit from clustering.  
  
## Increase the number of  HTTP concurrent connections allowed by changing the value for the maxconnection parameter  
 By default, the  HTTP adapters (including WCF-based HTTP adapters) open only two concurrent HTTP connections from each computer running BizTalk Server to any specific destination server.  
  
 This setting conforms to the IETF RFC for the HTTP 1.1 specification, and although it is suitable for user scenarios, it is not optimized for high throughput. The setting effectively throttles outbound  HTTP calls to each server to two concurrent sends from each computer running BizTalk Server.  
  
 To increase the number of concurrent connections, you can modify the value for the maxconnection parameter in the BizTalk Server configuration file, BTSNTSvc.exe.config (or BTSNTSvc64.exe.config for 64-bit hosts), on each BizTalk Server. You can increase this for the specific servers being called. As a rule of thumb, the value for the maxconnection parameter should be set to 12 * the number of CPUs or cores on the computer hosting the web application.  
  
> [!NOTE]  
>  Do not increase the value for the maxconnection parameter to such a large value that the Web server being called is overwhelmed with HTTP connections. After changing the value for the maxconnection parameter, perform stress testing by sending requests to each destination Web server to determine a value for maxconnection that will provide good performance  and HTTP sends without overwhelming the target Web servers.  
  
 The following is an example of the configuration for the maximum connections property:  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="24" />  
      <add address="*" maxconnection="48" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
 When setting the maxconnection property, HTTP, HTTPS, the web site IP address, and the port number can be specified. Other examples include:  
  
 **\<add address="<https://www.contoso.com>" maxconnection="24" /\>**   
**\<add address="<http://www.contoso.com:8080>" maxconnection="24" /\>**   
**\<add address="http://*IPAddress*" maxconnection="24" /\>**  For more information about tuning IIS and ASP.NET settings for Web services, see the "ASP.NET settings that can impact HTTP  Adapter performance" section of [Configuration Parameters that Affect Adapter Performance](http://go.microsoft.com/fwlink/?LinkID=154200) (<http://go.microsoft.com/fwlink/?LinkID=154200>) in BizTalk Server 2010 Help.  
  
## Manage ASP.NET thread usage or concurrently executing requests for Web applications that can host  isolated received locations, back-end Web services and WCF services  
 The number of worker and I/O threads (IIS 7.5 and IIS 7.0 in classic mode) or the number of concurrently executing requests (IIS 7.5 and 7.0 integrated mode) for an ASP.NET Web application that hosts isolated received locations, back-end Web services and WCF services should be modified under the following conditions:  
  
-   CPU utilization is not a bottleneck on the hosting Web server.  
  
-   The value of:  
  
    -   **ASP.NET Apps v4.0.30319 \Request Wait Time** or **ASP.NET Apps v4.0.30319 \Request Execution Time** performance counters is unusually high.  
  
    -   **ASP.NET Apps v2.0.50727\Request Wait Time** or **ASP.NET Apps v2.0.50727\Request Execution Time** performance counters is unusually high.  
  
-   An error similar to the following is generated in the Application log of the computer that hosts the Web application.  
  
    ```  
    Event Type: Warning  
    Event Source: W3SVC Event Category: None  
    Event ID: 1013  
    Date: 11/4/2010  
    Time: 1:03:47 PM  
    User: N/A  
    Computer: <ComputerName>  
    Description: A process serving application pool 'DefaultAppPool' exceeded time limits during shut down. The process id was '<xxxx>'  
    ```  
  
### Manage ASP.NET thread usage for Web applications that can host isolated received locations, back-end Web services and WCF services on IIS 7.5 and IIS 7.0 running in Classic mode  
 When the **autoConfig** value in the machine.config file of an IIS 7.5 and IIS 7.0 server running in Classic mode is set to **true**, ASP.NET 2.0  and ASP.NET 4 manages the number of worker threads and I/O threads that are allocated to any associated IIS worker processes.  
  
```  
<processModel autoConfig="true" />  
```  
  
 To manually modify the number of worker and I/O threads for an ASP.NET 2.0 and ASP.Net 4 Web application, open the associated machine.config file, and then enter new values for the **maxWorkerThreads** and **maxIoThreads** parameters.  
  
```  
<!-- <processModel autoConfig="true" /> -->  
    <processModel maxWorkerThreads="200" maxIoThreads="200" />  
```  
  
> [!NOTE]  
>  These values are for guidance only; ensure you test changes to these parameters.  
  
 For more information about tuning parameters in the machine.config file for an ASP.NET 2.0 Web application, see the Microsoft Knowledge Base article 821268 [Contention, poor performance, and deadlocks when you make Web service requests from ASP.NET applications](http://go.microsoft.com/fwlink/?LinkID=144169) (http://go.microsoft.com/fwlink/?LinkID=144169).  
  
### Manage the number of concurrently executing requests for ASP.NET 2.0 Web applications that can host isolated received locations, back-end Web services and WCF services on IIS 7.5 and IIS 7.0 running in Integrated mode  
 When ASP.NET 2.0 is hosted on IIS 7.5 and IIS 7.0 in integrated mode, the use of threads is handled differently than on  IIS 7.5 and IIS 7.0 in classic mode. When ASP.NET 2.0 is hosted on IIS 7.5 and IIS 7.0 in integrated mode, ASP.NET 2.0 restricts the number of concurrently executing **requests** rather than the number of **threads** concurrently executing requests. For synchronous scenarios this will indirectly limit the number of threads but for asynchronous scenarios the number of requests and threads will likely be very different. When running ASP.NET 2.0 on IIS 7.5 and IIS 7.0 in integrated mode, the **maxWorkerThreads** and **maxIoThreads** parameters in the machine.config file are not used to govern the number of running threads. Instead, the number of concurrently executing requests can be changed from the default value of 12 per CPU by modifying the value specified for **maxConcurrentRequestsPerCPU**. The **maxConcurrentRequestsPerCPU** value can be specified either in the reqistry or in the config section of an aspnet.config file. Follow these steps to change the default value for **maxConcurrentRequestsPerCPU** to govern the number of concurrently executing requests:  
  
 **To set the maxConcurrentRequestsPerCPU value in the registry**  
  
> [!WARNING]  
>  Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system. Use Registry Editor at your own risk. For more information about how to back up, restore, and modify the registry, see Microsoft Knowledge Base article 256986 [Windows registry information for advanced users](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729).  
  
> [!NOTE]  
>  This setting is global and cannot be changed for individual application pools or applications.  
  
1. Click **Start**, click **Run**, type **regedit.exe**, and then click **OK** to start Registry Editor.  
  
2. Navigate to **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0**  
  
3. Create the key by following these steps:  
  
   1.  On the **Edit** menu, click **New**, and then click **Key**.  
  
   2.  Type **maxConcurrentRequestsPerCPU**, and then press **ENTER**.  
  
   3.  Under the **maxConcurrentRequestsPerCPU** key, create a DWORD entry with the new value for maxConcurrentRequestsPerCPU.  
  
   4.  Close Registry Editor.  
  
   **To set the maxConcurrentRequestsPerCPU value for an application pool in the config section of an aspnet.config file**  
  
> [!NOTE]  
>  Microsoft .NET Framework 3.5 Service Pack 1 must be installed to accommodate setting the values below via configuration file. You can download Microsoft .NET Framework 3.5 Service Pack 1 from [Microsoft .NET Framework 3.5 Service Pack 1](http://go.microsoft.com/fwlink/?LinkID=136345) (http://go.microsoft.com/fwlink/?LinkID=136345).  
  
 Open the aspnet.config file for the application pool, and then enter new values for the **maxConcurrentRequestsPerCPU** and **requestQueueLimit** parameters.  
  
```  
<system.web>  
    <applicationPool maxConcurrentRequestsPerCPU="12" requestQueueLimit="5000"/>  
</system.web>  
```  
  
> [!NOTE]  
>  This value overrides the value specified for **maxConcurrentRequestsPerCPU** in the registry. The requestQueueLimit setting is the same as processModel/requestQueueLimit, except that the setting in the aspnet.config file will override the setting in the machine.config file.  
  
 For more information about configuring ASP.NET Thread Usage on IIS 7.0, see [Thomas Marquardt's Blog on ASP.NET Thread Usage on IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=157518) (http://go.microsoft.com/fwlink/?LinkId=157518).  
  
### Manage the number of concurrently executing requests for ASP.NET 4Web applications that can host isolated received locations, back-end Web services and WCF services on IIS 7.5 and 7.0 running in Integrated mode  
 With .NET Framework 4, the default setting for maxConcurrentRequestsPerCPU is 5000, which is a very large number and therefore will allow plenty of asynchronous requests to execute concurrently. For more information, see [\<applicationPool\> Element (Web Settings)](http://go.microsoft.com/fwlink/?LinkID=205339) (http://go.microsoft.com/fwlink/?LinkID=205339).  
  
 For IIS 7.5 and IIS 7.0 Integrated mode, a DWORD named MaxConcurrentRequestsPerCPU within HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0 determines the number of concurrent requests per CPU. By default, the registry key does not exist and the number of requests per CPU is limited to 5000.  
  
 **To set the maxConcurrentRequestsPerCPU value in the registry**  
  
> [!WARNING]  
>  Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system. Use Registry Editor at your own risk. For more information about how to back up, restore, and modify the registry, see Microsoft Knowledge Base article 256986 [Windows registry information for advanced users](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729).  
  
> [!NOTE]  
>  This setting is global and cannot be changed for individual application pools or applications.  
  
1. Click **Start**, click **Run**, type **regedit.exe**, and then click **OK** to start Registry Editor.  
  
2. Navigate to **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0**.  
  
3. Create the key by following these steps:  
  
   1.  On the **Edit** menu, click **New**, and then click **Key**.  
  
   2.  Type **maxConcurrentRequestsPerCPU**, and then press **ENTER**.  
  
   3.  Under the **maxConcurrentRequestsPerCPU** key, create a DWORD entry with the new value for maxConcurrentRequestsPerCPU.  
  
   4.  Close Registry Editor.  
  
   **To set the maxConcurrentRequestsPerCPU value for an application pool in the config section of an aspnet.config file**  
  
> [!NOTE]  
>  Microsoft .NET Framework 4 must be installed to accommodate setting the values below via configuration file. You can download Microsoft .NET Framework 4 from [Microsoft .NET Framework 4 (Web Installer)](http://go.microsoft.com/fwlink/?LinkID=189318) (http://go.microsoft.com/fwlink/?LinkID=189318).  
  
-   Open the aspnet.config file for the application pool, and then enter new values for the **maxConcurrentRequestsPerCPU** and **requestQueueLimit** parameters.  
  
     The values in the following example are the default values.  
  
    ```  
    <system.web>  
        <applicationPool maxConcurrentRequestsPerCPU="5000" requestQueueLimit="5000"/>  
    </system.web>  
    ```  
  
> [!NOTE]  
>  This value overrides the value specified for **maxConcurrentRequestsPerCPU** in the registry. The **requestQueueLimit** setting is the same as processModel/requestQueueLimit, except that the setting in the aspnet.config file will override the setting in the machine.config file.  
  
## Define CLR hosting thread values for BizTalk host instances  
 Because a Windows thread is the most basic executable unit available to a Windows process, it is important to allocate enough threads to the .NET thread pool associated with an instance of a BizTalk host to prevent thread starvation. When thread starvation occurs, there are not enough threads available to perform the requested work that negatively impacts performance. At the same time, care should be taken to prevent allocating more threads to the.NET thread pool associated with a host than is necessary. The allocation of too many threads to the .NET thread pool associated with a host may increase context switching. Context switching occurs when the Windows kernel switches from running one thread to a different thread, which incurs a performance cost. Excessive thread allocation can cause excessive context switching, which will negatively impact overall performance. The default number of threads allocated to a BizTalk host instance’s .NET thread pool depends on which version of the .NET Framework is installed. The .NET Framework 4 and the .NET Framework 3.5 SP1 greatly increased the defaults, which can cause excessive thread allocation on the BizTalk Server computers and excessive lock contention on the MessageBox database.  
  
 Using the **BizTalk Settings Dashboard**, you can modify the default value for the number of Windows threads available in the .NET thread pool associated with an instance of a BizTalk host. For more information about how to modify .NET CLR settings, see [How to Modify .NET CLR Settings](http://go.microsoft.com/fwlink/?LinkID=205344) (http://go.microsoft.com/fwlink/?LinkID=205344). .NET CLR Settings are per-core CPU.  
  
> [!NOTE]  
>  **Worker threads** are used to handle queued work items and **I/O threads** are dedicated callback threads associated with an I/O completion port to handle a completed asynchronous I/O request.  
  
|Threading settings|Default value|Recommended value|  
|------------------------|-------------------|-----------------------|  
|Maximum IO Threads|250|250|  
|Maximum Worker Threads|25|100 **Important:**  Increasing this value beyond 100 can have an adverse effect on the performance of the SQL Server computer hosting the BizTalk Server MessageBox database. When this problem occurs, SQL Server may encounter a deadlock condition. We recommend not increasing this parameter beyond a value of 100.|  
|Minimum IO Threads|25|25|  
|Minimum Worker Threads|5|25|  
  
> [!NOTE]  
>  The recommended values are not absolutes and may need to be adjusted depending on the BizTalk application. Change one parameter at a time, and then measure the impact on the performance and stability of the BizTalk platform before making additional changes.  
  
> [!NOTE]  
>  These values are implicitly multiplied by the number of processors on the server. For example, setting the **MaxWorkerThreads** entry to a value of 100 would effectively set a value of 400 on a 4 CPU server.  
  
## Disable BizTalk Server Group-level tracking  
 Tracking incurs performance overhead within BizTalk Server as data has to be written to the MessageBox database and then asynchronously moved to the BizTalk Tracking database. The following considerations apply when configuring tracking in a production BizTalk Server environment:  
  
- As a rule of thumb, if tracking is not a business requirement, then disable group-level tracking to reduce overhead and increase performance.  
  
   To disable BizTalk Server group-level tracking, perform the following steps:  
  
  1.  In the **BizTalk Server Administration Console**, expand **BizTalk Server Administration**, right-click **BizTalk Group**, and then click **Settings**.  
  
  2.  In the BizTalk Settings Dashboard dialog box, on the Group page, clear the **Enable group-level tracking** check box.  
  
  3.  Click **OK** to apply the modifications and exit the Settings Dashboard.  
  
- Only use message body tracking if necessary. Depending on message throughput and message size, message body tracking can cause significant overhead. While BizTalk activity tracking has obvious benefits for debugging and auditing, it also has considerable performance and scalability implications. Therefore, you should track only data that is strictly necessary for debugging and security reasons, and avoids tracking redundant information.  
  
- By default, the following tracking options are enabled for orchestrations:  
  
  - Orchestration start and end  
  
  - Message send and receive  
  
  - Shape start and end  
  
    The orchestration tracking option “Shape start and end” incurs significant overhead and should not be enabled in a production environment where high throughput is necessary. Orchestration tracking options are accessible in the BizTalk Administration console on the **Tracking** page of the Orchestration Properties dialog box.  
  
  For more information about configuring tracking, see [Configuring Tracking Using the BizTalk Server Administration Console](http://go.microsoft.com/fwlink/?LinkId=158021) (http://go.microsoft.com/fwlink/?LinkId=158021).  
  
## Decrease the purging period for the DTA Purge and Archive job from 7 days to 2 days in high throughput scenarios  
 By default, the purging interval for tracking data in BizTalk Server is set to 7 days. In a high throughput scenario, this can result in an excessive build up of data in the Tracking database, which will eventually impact the performance of the MessageBox and in turn negatively impact message processing throughput.  
  
 In high throughput scenarios, reduce the hard and soft purging interval from the default of 7 days to 2 days. For more information about configuring the purging interval, see [How to Configure the DTA Purge and Archive Job](http://go.microsoft.com/fwlink/?LinkID=153814) (http://go.microsoft.com/fwlink/?LinkID=153814) in the BizTalk Server 2010 Help.  
  
## Configure the %temp% path for the BizTalk Service account to point to a separate disk or LUN  
 This should be done because BizTalk uses the temp location to stream files to disk when performing complex mapping operations.  
  
## Install the latest service packs  
 The latest service packs for both BizTalk Server and the .NET Framework should be installed, as these contain fixes that can correct performance issues you may encounter.  
  
## Performance optimizations in the BizTalk Server documentation  
 Apply the following recommendations from the BizTalk Server documentation as appropriate:  
  
-   [Troubleshooting MessageBox Latency Issues](http://go.microsoft.com/fwlink/?LinkId=158019) (http://go.microsoft.com/fwlink/?LinkId=158019)  
  
-   [Identifying Performance Bottlenecks](http://go.microsoft.com/fwlink/?LinkID=154238) (http://go.microsoft.com/fwlink/?LinkID=154238)  
  
-   [Avoiding DBNETLIB Exceptions](http://go.microsoft.com/fwlink/?LinkID=155308) (http://go.microsoft.com/fwlink/?LinkID=155308)  
  
-   [Avoiding TCP/IP Port Exhaustion](http://go.microsoft.com/fwlink/?LinkID=153240) (http://go.microsoft.com/fwlink/?LinkID=153240)  
  
-   [Setting the EPM Threadpool Size](http://go.microsoft.com/fwlink/?LinkId=158020) (http://go.microsoft.com/fwlink/?LinkId=158020)  
  
## See Also  
 [Optimizing BizTalk Server Performance](../technical-guides/optimizing-biztalk-server-performance.md)