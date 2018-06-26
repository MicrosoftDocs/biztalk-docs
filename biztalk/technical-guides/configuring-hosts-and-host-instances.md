---
title: "Configuring Hosts and Host Instances | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a36a73a4-cc5f-47d6-b56f-7871684c4489
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Hosts and Host Instances
A BizTalk Host represents a logical set of zero or more run-time processes in which you can deploy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services and artifacts (such as adapter handlers, receive locations, and orchestrations). A host instance is the physical instance of a host on a computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For more information about BizTalk Hosts and host instances, see [Hosts](http://go.microsoft.com/fwlink/?LinkId=154189) (<http://go.microsoft.com/fwlink/?LinkId=154189>) and [Host Instances](http://go.microsoft.com/fwlink/?LinkId=154190) (<http://go.microsoft.com/fwlink/?LinkId=154190>).  
  
 For more information about managing BizTalk Hosts and host instances, see [Managing BizTalk Hosts and Host Instances](http://go.microsoft.com/fwlink/?LinkId=154191) (http://go.microsoft.com/fwlink/?LinkId=154191).  
  
 For information about how to configure a dedicated tracking host, see [Configuring a Dedicated Tracking Host](../technical-guides/configuring-a-dedicated-tracking-host.md).  
  
## Separating Host Instances by Functionality  
 In addition to the high availability aspects of the host instance configuration, you should separate sending, receiving, processing, and tracking functionality into multiple hosts. This provides flexibility when configuring the workload in your BizTalk group and is the primary means of distributing processing across a BizTalk group. This also allows you to stop one host without affecting other hosts. For example, you may want to stop sending messages to let them queue up in the MessageBox database, while still allowing the inbound receiving of messages to occur.  
  
 Separating host instances by functionality also provides the following benefits:  
  
- Each host instance has its own set of resources such as memory, handles, and threads in the .NET thread pool.  
  
- Multiple BizTalk Hosts will also reduce contention on the MessageBox database host queue tables since each host is assigned its own work queue tables in the MessageBox database.  
  
- Throttling is implemented in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] at the host level. This allows you to set different throttling characteristics for each host.  
  
- Security is implemented at the host level; each host runs under a discrete Windows identity. This would allow you, for example, to give **Host_A** access to **FileShare_B**, while not allowing any of the other hosts to access the file share.  
  
  > [!NOTE]  
  >  While there are benefits to creating additional host instances, there are also potential drawbacks if too many host instances are created. Each host instance is a Windows service (BTSNTSvc.exe or BTSNTSvc64.exe), which generates additional load against the MessageBox database and consumes computer resources (such as CPU, memory, threads).  
  
  For more information about modifying [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Host properties, see [How to Modify Host Properties](http://go.microsoft.com/fwlink/?LinkId=154192) (<http://go.microsoft.com/fwlink/?LinkId=154192>).  
  
##  <a name="BKMK_MemLimit"></a> Maximum Practical Limits of Memory Usage of a 32-bit BizTalk Host Instance  
 32-bit processes on 32-bit Windows operating system with /3GB set have 3 gigabytes (GB) of addressable memory if the process is "large address aware" (that is, the executable has the IMAGE_FILE_LARGE_ADDRESS_AWARE flag set in the image header).  The BizTalk host process, being "large address aware", can address 3 GB of memory on Windows operating system with /3GB set.  Similarly, 32-bit processes on 64-bit Windows operating system (AMD64) have 4 GB of addressable memory, if the process is "large address aware".  Again, the BizTalk host process, being "large address aware", can address 4 GB of memory when running as a 32-bit process on 64-bit Windows operating system. 64-bit processes on 64-bit Windows operating system (AMD64) have 8 terabytes of addressable memory.  
  
 Even though the maximum memory addressable by a process on a 32-bit Windows operating system (without the /3GB switch) is 2 GB, a .NET application (such as a BizTalk host instance) will receive out of memory errors before the "virtual bytes" reaches 2 GB. The table below summarizes this and includes the practical limits for virtual bytes and private bytes.  
  
|Process|Windows OS|Addressable Memory (with a Large Address Aware process)|Practical Limit for Virtual Bytes|Practical Limit for PrivateBytes|  
|-------------|----------------|---------------------------------------------------------------|---------------------------------------|--------------------------------------|  
|32-bit|32-bit|2 GB|1400 MB|800 MB|  
|32-bit|32-bit with /3GB|3 GB|2400 MB|1800 MB|  
|32-bit|64-bit|4 GB|3400 MB|2800 MB|  
|64-bit|64-bit|8 terabytes|-|-|  
  
 For more information, see:  
  
-   [ASP.NET Performance Monitoring, and When to Alert Administrators](http://go.microsoft.com/fwlink/?LinkId=151856) (http://go.microsoft.com/fwlink/?LinkId=151856)  
  
-   [Memory Limits for Windows Releases](http://go.microsoft.com/fwlink/?LinkId=151857) (http://go.microsoft.com/fwlink/?LinkId=151857)  
  
## See Also  
 [Checklist: Configuring BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)   
 [Configuring a Dedicated Tracking Host](../technical-guides/configuring-a-dedicated-tracking-host.md)