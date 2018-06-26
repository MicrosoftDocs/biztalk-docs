---
title: "Optimizing IIS Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6722a2ee-3704-4aaa-9b0d-cef97bcb9a04
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing IIS Performance
## Apply IIS configuration options to improve IIS performance  
 Internet Information Services (IIS) exposes numerous configuration parameters that affect IIS performance. This topic describes several of these parameters and provides general guidance for setting the parameter values to improve IIS performance.  
  
### Log only essential information or completely disable IIS logging  
 IIS logging should be minimized or even disabled in a production environment. To disable logging follow these steps:  
  
1.  Click **Start**, point to **All Programs**, click **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In the **Connections** pane, click to expand **Sites**, click to select the Web site for which you would like to disable logging, click to select **Features View**, and then double-click the **Logging** feature.  
  
3.  Click **Disable** in the **Actions** pane to disable logging for this Web site.  
  
### Disable IIS ASP debugging in production environments  
 IIS ASP debugging should be disabled in a production environment. To disable IIS ASP debugging follow these steps: In the **Connections** pane, click to expand **Sites**, click to select the web site for which you would like to disable ASP debugging, click to select **Features View**, and then double-click the **ASP** feature. Click to expand **Compilation**, click to expand **Debugging Properties**, and verify that both **Enable Client-side Debugging** and **Enable Server-side Debugging** are set to **False**.  
  
1. Click **Start**, point to **All Programs**, click **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2. In the **Connections** pane, click to expand **Sites**, click to select the web site for which you would like to disable ASP debugging, click to select **Features View**, and then double-click the **ASP** feature.  
  
3. Click to expand **Compilation**, click to expand **Debugging Properties**, and verify that both **Enable Client-side Debugging** and **Enable Server-side Debugging** are set to **False**.  
  
4. If necessary, click **Apply** in the **Actions** pane.  
  
   Disable debugging for ASP.NET Applications and Web Services by specifying the \<compilation debug="false"\> section in the web.config file for the web application.  
  
### Tune the value of the ASP Threads Per Processor Limit property  
 The ASP **Threads Per Processor Limit** property specifies the maximum number of worker threads per processor that IIS creates. Increase the value for the Threads Per Processor Limit until the processor utilization meets at least 50 percent or above. This setting can dramatically influence the scalability of your Web applications and the performance of your server in general. Because this property defines the maximum number of ASP requests that can execute simultaneously, this setting should remain at the default value unless your ASP applications are making extended calls to external components. In this case, you may increase the value of Threads Per Processor Limit. Doing so allows the server to create more threads to handle more concurrent requests. The default value of Threads Per Processor Limit is 25. The maximum recommended value for this property is 100.  
  
 To increase the value for the Threads Per Processor Limit follow these steps:In the **Connections** pane, select the web server, click to select **Features View**, and then double-click the **ASP** feature.  
  
1. Click **Start**, point to **All Programs**, click **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2. In the **Connections** pane, select the web server, click to select **Features View**, and then double-click the **ASP** feature.  
  
3. Click to expand **Limits Properties** under **Behavior**, click **Threads Per Processor Limit**, enter the desired value for **Threads Per Processor Limit** and click **Apply** in the **Actions** pane.  
  
   For more information about how to modify the properties in the \<limits\> element of the IIS 7.5/7.0 \<asp\> element, see [ASP Limits \<limits\>](http://go.microsoft.com/fwlink/?LinkId=157483) (http://go.microsoft.com/fwlink/?LinkId=157483).  
  
> [!NOTE]  
>  Because this property can only be applied at the server level, modification of this property affects all Web sites that run on the server.  
  
### Tune the value of the ASP Queue Length property  
 The goal of tuning this property is to ensure good response time while minimizing how often the server sends the HTTP 503 (Server Too Busy) error to clients when the ASP request queue is full. If the value of ASP Queue Length property is too low, the server will send the HTTP 503 error with greater frequency. If the value of ASP Queue Length property is too high, users might perceive that the server is not responding when in fact their request is waiting in the queue. By watching the queue during periods of high traffic, you should discern a pattern of web request peaks and valleys. Make note of the peak value, and set the value of the ASP Queue Length property just above the peak value. Use the queue to handle short-term spikes, ensure response time, and throttle the system to avoid overload when sustained, unexpected spikes occur. If you do not have data for adjusting the ASP Queue Length property, a good starting point will be to set a one-to-one ratio of queues to total threads. For example, if the ASP Threads Per Processor Limit property is set to 25 and you have four processors (4 * 25 = 100 threads), set the ASP Queue Length property to 100 and tune from there.  
  
 To increase the value for the Queue Length property follow these steps:  
  
1. Click **Start**, point to **All Programs**, click **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2. In the **Connections** pane, select the Web server, click to select **Features View**, and then double-click the **ASP** feature.  
  
3. Click to expand **Limits Properties** under **Behavior**, click **Queue Length**, enter the desired value for **Queue Length** and then click **Apply** in the **Actions** pane.  
  
   For more information about how to modify the properties in the \<limits\> element of the IIS 7.5/7.0 \<asp\> element, see [ASP Limits \<limits\>](http://go.microsoft.com/fwlink/?LinkId=157483) (http://go.microsoft.com/fwlink/?LinkId=157483).  
  
> [!NOTE]  
>  Because this property can only be applied at the server level, modification of this property affects all Web sites that run on the server.  
  
### Tune the MaxPoolThreads registry entry  
 This setting specifies the number of pool threads to create per processor. Pool threads watch the network for requests and process incoming requests. The MaxPoolThreads count does not include threads that are consumed by ISAPI applications. Generally, you should not create more than 20 threads per processor. MaxPoolThreads is a REG_DWORD registry entry located at HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\InetInfo\Parameters\ with a default value of 4.  
  
### Disable WCF services tracing  
 Use the Configuration Editor Tool (SvcConfigEditor.exe) to disable WCF services tracing in a production environment. For more information about the Configuration Editor Tool, see [Configuration Editor Tool (SvcConfigEditor.exe)](http://go.microsoft.com/fwlink/?LinkID=127070) (http://go.microsoft.com/fwlink/?LinkID=127070).  
  
### Configure ASP.NET 2.0 MaxConcurrentRequests for IIS 7.5/7.0 Integrated mode  
 When ASP.NET 2.0 is hosted on IIS 7.5/7.0 in Integrated Mode, the use of threads is handled differently than on IIS 7.5/7.0 in Classic Mode. When ASP.NET 2.0 is hosted on IIS 7.5 in Integrated mode, ASP.NET 2.0 restricts the number of concurrently executing requests instead of the number of threads concurrently executing requests. For synchronous scenarios, this will indirectly limit the number of threads because the number of requests will be the same as the number of threads. But for asynchronous scenarios, the number of requests and threads will likely be very different because you could have far more requests than threads. When you run ASP.NET 2.0 on IIS 7.5 in integrated mode, the minFreeThreads and minLocalRequestFreeThreads of the “httpRuntime” element in the machine.config are ignored. For IIS 7.5 Integrated mode, a DWORD named MaxConcurrentRequestsPerCPU within HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\2.0.50727.0 determines the number of concurrent requests per CPU. By default, the registry key does not exist and the number of requests per CPU is limited to 12. .NET Framework 3.5 SP1 includes an update to the v2.0 binaries that supports configuring IIS application pools via the aspnet.config file. This configuration applies to integrated mode only (Classic/ISAPI mode ignores these settings).The new aspnet.config config section with default values is listed below:  
  
```  
<system.web>  
   <applicationPool maxConcurrentRequestsPerCPU="12" maxConcurrentThreadsPerCPU="0" requestQueueLimit="5000"/>  
</system.web>  
```  
  
 In IIS 7.5 Integrated Mode, the maxWorkerThreads and the maxIoThreads parameters in the “processModel” section of the machine.config file are not used to govern the number of running requests, per se, but they are still used to govern the size of the CLR thread pool used by ASP.NET. When the “processModel” section of the machine.config has “autoConfig=true” (which is the default setting), this will give the application pool up to 100 worker threads (MaxWorkerThreads) per logical CPU. So a common commodity server with 2 dual-core CPUs would have 400 MaxWorkerThreads. This should be sufficient for all but the most demanding applications.  
  
 For more information about configuring ASP.NET Thread Usage on IIS 7.5, see [Thomas Marquardt's Blog on ASP.NET Thread Usage on IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=157518) (http://go.microsoft.com/fwlink/?LinkId=157518).  
  
### Configure ASP.NET 4 MaxConcurrentRequests for IIS 7.5/7.0 Integrated mode  
 With .NET Framework 4, the default setting for maxConcurrentRequestsPerCPU is 5000 which is a very large number and therefore will allow plenty of asynchronous requests to execute concurrently. For more information, see [\<applicationPool\> Element (Web Settings)](http://go.microsoft.com/fwlink/?LinkID=205339) (http://go.microsoft.com/fwlink/?LinkID=205339).  
  
 For IIS 7.5/7.0 Integrated mode, a DWORD named MaxConcurrentRequestsPerCPU within HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ASP.NET\4.0.30319.0 determines the number of concurrent requests per CPU. By default, the registry key does not exist and the number of requests per CPU is limited to 5000.  
  
### Enable IIS HTTP compression  
 To more efficiently use available bandwidth, enable IIS HTTP compression. HTTP compression provides faster transmission time between compression-enabled browsers and IIS, regardless of whether your content is served from local storage or a UNC resource.  
  
-   **To configure compression at the Web server level:**  
  
    1.  Click **Start**, point to **All Programs**, click **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
    2.  In the **Connections** pane, select the Web server, click to select **Features View**, and then double-click the **Compression** feature.  
  
    3.  Set the desired compression options and then click **Apply** in the **Actions** pane.  
  
-   **To configure compression at the Web site level:**  
  
    1.  Click **Start**, point to **All Programs**, click **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
    2.  In the **Connections** pane, click to expand **Sites**, click to select the Web site for which you would like to configure compression, click to select **Features View**, and then double-click the **Compression** feature.  
  
    3.  Set the desired compression options and then click **Apply** in the **Actions** pane.  
  
## See Also  
 [Optimizing Performance](../technical-guides/optimizing-performance.md)