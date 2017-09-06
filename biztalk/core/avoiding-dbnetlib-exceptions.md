---
title: "Avoiding DBNETLIB Exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5fbee0cf-d249-4d98-8d16-168ded32f9f1
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Avoiding DBNETLIB Exceptions
DBNetLib (Database Network Library) errors occur when the BizTalk Server runtime is unable to communicate with either the MessageBox or Management databases. When this occurs, the BizTalk Server runtime instance that catches the exception shuts down and then cycles every minute to check to see if the database is available.  
  
 The most common cause of a DBNetLib error is when one of the (possibly many) MessageBox database servers becomes extremely busy and further attempts to communicate with it result in a timeout, which causes a DBNetLib exception.  
  
 In addition to the case where the MessageBox database is simply very busy, the DBNetLib error can occur in a production environment when BizTalk database servers hosting one of more MessageBox databases become I/O (Input/Output) bound.  
  
 This topic describes conditions that can lead to DBNetLib errors and recommendations for avoiding these errors.  
  
## Cause and Resolution for the DBNetLib error  
  
### Symptoms of a DBNetLib error  
 A Microsoft BizTalk Server host instance terminates and then restarts itself, and errors that are similar to the following are written to the BizTalk Server Application log:  
  
```  
Event Type:Warning  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:5410  
Computer:BIZTALKSERVER  
Description:  
An error occurred that requires the BizTalk service to terminate. The most common causes are the following:  
 1) An unexpected out of memory error.  
 OR  
 2) An inability to connect or a loss of connectivity to one of the BizTalk databases.   
 The service will shutdown and auto-restart in 1 minute. If the problematic database remains unavailable, this cycle will repeat.  
  
 Error message: [DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation.  
 Error source:    
  
 BizTalk host name: BizTalkHost  
 Windows service name: BTSSvc$BizTalkHost   
  
---------------------------------------------------------  
Event Type:Error  
Event Source:BizTalk Server <version>  
Event Category:BizTalk Server <version>   
Event ID:6913  
Computer:BIZTALKSERVER  
Description:  
An attempt to connect to "BizTalkMsgBoxDb" SQL Server database on server "SQLSERVER " failed.  
 Error: "[DBNETLIB][ConnectionWrite (send()).]General network error. Check your network documentation."  
```  
  
### BizTalk database servers hosting MessageBox databases becoming I/O bound  
 BizTalk servers communicate and act directly with the database servers hosting the MessageBox databases. If any of the database servers hosting the MessageBox databases get too consumed and gets into an I/O (Input/Output) bound situation, then it might become unresponsive. One of the BizTalk servers might in turn lose connectivity with one of those database servers, and a DBNetLib error will occur.  
  
 Our tests show that a highly consumed database server becomes I/O bound when its physical disk’s "%Idle time" continues to drop and reaches below 10%. If the “%Idle time” continues to drop below that level, then this is an indication that your database server is likely to become unresponsive.  
  
#### Cause  
 There are several reasons that can cause the database servers hosting the MessageBox databases to become I/O bound, some of these are the following:  
  
-   If the database machine hosting the MessageBox database is bound by low hardware specifications such as: low memory, number and speed of processors etc.  
  
-   If the physical disk on the database machine hosting a MessageBox database is being shared by other highly consumed databases. In cases when several databases (including the MessageBox) are being highly consumed at the same time, the physical disk can get into an I/O bound situation.  
  
     An example of such a situation is the following:  
  
     Our tests show that the database server hosting the BizTalkDTADb and/or BAM databases sometimes consume high percentages of a physical disk’s %Disk Read and Write Times. When the database server disk that hosts a MessageBox database is being shared by another highly consumed database such as BizTalkDTADb or BAM, and if both databases are highly consumed simultaneously, they might cause the database server physical disk to become I/O bound and then unresponsive.  
  
-   If BizTalkDTADb and one or more of the MessageBox databases are sharing the same physical disk on the database server, if archiving and purging is not being run frequently, the disk might become I/O bound.  
  
#### Resolution  
 Ensure the database server(s) hosting the BizTalk MessageBox(s) do not get into a situation where they become highly consumed and possibly unresponsive.  
  
 Some of the primary causes of a server disk becoming highly consumed are listed below along with recommendations on how to mitigate this problem.  
  
##### Low Hardware Specs  
 Our tests show that the server starts getting more consumed when its hardware specifications cannot keep up with the amount of load it’s trying to process. With lower hardware specs, the system gets overwhelmed quickly by the amount of activities happening on the databases. This might cause the server’s %Disk Read and Write Times to continue increasing without stabilizing, also the disk’s %Idle time to continue to decrease and become lower than 10%, and this might cause your database server to become unresponsive.  
  
 Depending on the amount of activities and load you have on your BizTalk deployment, if you find that you are getting unresponsive database servers during to high loads, you should consider upgrading the following parts in your database servers: number of CPUs, memory, and connecting to a SAN. Of course, you should do the proper diagnosis to figure out which part (memory, number of CPUs etc.) is the bottleneck that needs to be upgraded in your hardware.  
  
##### Sharing one server or disk for more than one group of BizTalk databases  
 As mentioned previously, databases other than MessageBoxes, such as the BizTalk Tracking (BizTalkDTADb) database and BAM databases, might consume high cycles on a server’s physical disk. So, if those databases happen to share the same physical disk with the MessageBox databases, then they might choke the disk and make it unresponsive, which again might cause BizTalk servers to loose connectivity with the MessageBox databases and thus hit DBNetLib.  
  
 It is highly recommended that you separate any database expected to have high consumption of the server’s physical disk from the BizTalk MessageBox(s), so they share different physical disks (or separate them on different servers). It is recommended that you separate the BizTalkDTADb and BAM databases on their own separate drives/servers from the MessageBox(s), and it is also recommended to have each MessageBox database (in the case there is more than one) on it’s own disk.  
  
##### Archiving and Purging  
 In the case when you have BizTalkDTADb and MessageBox databases sharing the same disk on the same server, you must archive and purge your BizTalkDTADb databases regularly, otherwise they will grow indefinitely.  
  
 Testing indicates that it is good practice to archive and purge periodically, but if you run under higher loads than normal then you might want to consider archiving and purging more frequently. If the BizTalkDTADb database growth is not maintained regularly, then when these actions are finally performed they may take considerable time and consume most of the available database server resources while they are running.