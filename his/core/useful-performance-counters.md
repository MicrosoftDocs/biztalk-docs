---
title: "Useful Performance Counters2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93e022b8-e7f6-46d7-8de1-fe235db17a6e
caps.latest.revision: 3
---
# Useful Performance Counters
Performance counters allow you to see where computer resources are being used. The counters described below provide valuable information for evaluating the demand on, and performance of, [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] components.  
  
-   **Memory: Pages/sec**  
  
     In order to understand memory load on a Windows Server, you must first understand paging, which is a technique for implementing virtual memory. Paging is switching blocks (pages) of program instructions or data back and forth between memory and disk. Paging is carried out as needed by the virtual memory manager in Windows.  
  
     Pages/sec is the number of pages read from the disk or written to the disk because they were not in memory when needed (that is, the number of page faults that required disk access). The counter includes paging traffic generated when the cache accesses file data for applications.  
  
     Pages/sec is the primary counter for determining whether your server is paging excessively. As this counter goes up, server responsiveness slows because of the time required for disk access (reading or writing). A server dedicated to communications should be equipped with enough physical memory so that little paging is required.  
  
     The highest acceptable value for pages/sec varies from system to system. One way to judge whether system load is causing too much paging is to observe whether processor activity drops significantly as paging increases. This indicates that the system is occupied with switching pages rather than with actually processing instructions.  
  
     The primary ways to correct excessive paging are to add more physical memory to the server or to decrease the demand on the server. Demand can be decreased by narrowing the variety of tasks that a server must perform or by decreasing the number of users accessing a server. For example, an overloaded multipurpose server with file, print, and Host Integration Server demands, could be dedicated to Host Integration Server traffic only, or user loads placed on one server could be divided between two servers (load balancing). In any case of memory overload, adding physical memory may provide the needed performance increase.  
  
     A secondary way to decrease the impact of paging is to upgrade the disk system. This includes installing a faster disk, installing a second disk, using RAID striping, or similar upgrades. This upgrading does not decrease paging (pages/sec), but speeds up the paging process itself. For example, replacing a slow IDE disk with a faster SCSI disk may make a given paging rate, perhaps 20 – 40 pages/sec acceptable.  
  
-   **System: %Total Processor Time and Processor: %Processor Time**  
  
     System: %Total Processor Time is the percentage of elapsed time during which the system processors are busy. It can be viewed as the fraction of total processor time spent doing useful work. Values of 60 – 80 percent during typical loads are good values because they allow some reserve for peak loads. However, when the processor stays at 100 percent for periods of time, this may indicate a processor bottleneck. On a multiprocessor system, you can view **Processor: %Processor Time** for each processor to see how the load is distributed among processors.  
  
     One useful way to view **Total Processor Time** values is in Chart view, along with counters indicating increases and decreases in user load. For user load, such counters include **Host Integration Server Logical Unit Sessions: Throughput Bytes/Sec**, and **Host Integration Server Adapter \<*adaptername>*: Throughput Frames/Sec.** These two counters are available only when there is Host Integration Server activity. For example, you might notice that during a period of peak demand for logical unit sessions, Total Processor Time reaches 100 percent and stays there. This could indicate that the Host Integration Server computer is reaching peak capacity and that any additional demand might require additional processors or additional servers.  
  
     It may also be helpful to view **System: %Total Processor** Time along with any other counters related to the servers major functions. For example, when a Host Integration Server computer is also a file server, the **Server: Server Sessions** counter can be helpful. Other counters that may help you analyze the sources of processor activity are **Process: %Processor Time** for processes you think are relevant, as well as **System: Total Interrupts/sec**. Also, if your client computers use TCP/IP, consider looking at **TCP: Connections Established**.  
  
-   **System: Total Interrupts/sec and Processor: Interrupts/sec**  
  
     System: Total Interrupts/sec is the rate at which the computer is receiving and servicing device interrupts. Device interrupts are the signals that a device sends to a processor to indicate that a task is complete or the device requires attention. Some devices that may generate interrupts are adapters, network adapters, the system timer (clock), and the mouse. **System: Total Interrupts/sec** provides an indication of how busy these devices are on a computer-wide basis.  
  
     Similarly, for each processor, **Processor: Interrupts/sec** is the rate at which the processor is receiving device interrupts.  
  
     Normal thread execution is suspended during interrupts. An interrupt may cause the processor to switch to another, higher-priority thread. Clock interrupts are periodic and frequent (on the order of 100 per second); they create a background of interrupt activity.  
  
     These counters can help indicate the general demand on a server, and may be useful when combined with processor and memory data, such as **System: %Total Processor Time and Memory: Pages/sec.**  
  
-   **SNA Connections: Throughput Bytes/Sec**  
  
-   **SNA Logical Unit Sessions: Throughput Bytes/Sec**  
  
-   **SNA Adapter adaptername: Throughput Frames/Sec**  
  
     These counters provide an indication of Host Integration Server activity. When observing these counters, it may also be useful to start the SNA Manager and double-click the same server being observed in System Monitor. You can see the number of users and sessions that correlate with a particular level of Host Integration Server activity. This information, combined with data about the processor and memory load, can help you understand the load and performance on your servers. Low throughput does not necessarily mean poor performance, but instead may simply indicate that current activity is low.  
  
     Measurement of frames/second may provide a better indicator of server load than bytes per second, because server overhead for interrupt handling and message processing increases per frame, not per byte. In other words, a large frame with many bytes requires about the same overhead as a small frame with fewer bytes.  
  
-   **SNA Connections: Data Bytes Received/Sec**  
  
-   **SNA Connections: Data Bytes Transmitted/Sec**  
  
-   **SNA Logical Unit Sessions: Data Bytes Received/Sec**  
  
-   **SNA Logical Unit Sessions: Data Bytes Transmitted/Sec**  
  
-   **SNA Adapter adaptername: Data Bytes Received/Sec**  
  
-   **SNA Adapter adaptername: Data Bytes Transmitted/Sec**  
  
-   **SNA Adapter adaptername: Frames Received/Sec**  
  
-   **SNA Adapter adaptername: Frames Transmitted/Sec**  
  
-   **SNA Adapter adaptername: Throughput Bytes/Sec**  
  
     These counters provide additional detail about Host Integration Server activity when used with the previous three counters.  
  
-   **SNA Adapter adaptername: Adapter Failures**  
  
-   **SNA Adapter adaptername: Connection Failures**  
  
-   **SNA Adapter adaptername: Successful Connects**  
  
     These counters may be useful for detecting patterns in which connections or adapters fail for short periods and then return to normal. Event Logs can provide more information about causes of failure. You might also want to set up System Monitor alerts with these counters, so that an alert is triggered if too many failures occur.  
  
## See Also  
 [System Monitor Overview](../core/system-monitor-overview.md)   
 [System Monitor](../core/system-monitor.md)