---
description: "Learn more about: Troubleshooting MessageBox Latency Issues"
title: "Troubleshooting MessageBox Latency Issues"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Troubleshooting MessageBox Latency Issues
In a perfect world, all messages would be processed and delivered as soon as they were published to the MessageBox database and the MessageBox database would never grow to an excessive size. Any messages in the MessageBox that were no longer referenced would immediately be removed by the SQL agent jobs that periodically clean up the MessageBox database tables.  
  
 In real world scenarios, however, messages are not typically received in a predictable, linear fashion and the SQL agent jobs require time to clean up the MessageBox database tables.  
  
 Therefore, in some scenarios; the MessageBox can grow fairly large very quickly.  
  
 The following items can cause the MessageBox to grow excessively large and hinder overall performance:  
  
-   **The Biztalk Host instance that has the "allow Host tracking" option set is stopped**. This is the host that is responsible for moving the tracking data from the MessageBox database to the Biztalk Tracking database(BizTalkDTADb).  
  
-   **SQL Server Agent is not running** This can happen if the SQL jobs responsible for moving data from the MessageBox database to the BizTalkDTADb database [subsequently purging the moved data in the MessageBox] are not running. It is imperative the SQL Agent Service be running all the time to avoid this problem.  
  
-   **SQL Server Jobs are disabled** Even if the SQL Server Agent is running, it is imperative that none of the default SQL Server jobs be disabled.  
  
-   **BizTalkDTADb database grows excessively** This can happen if the BizTalkDTADb database grows very large, causing inserts into the BizTalkDTADb database to take longer. When this happens the movement of data by Tracking Data Delivery Service (TDDS) slows down, causing a backlog build up in the MessageBox database. To avoid this problem it is important to run the SQL server archive and purge jobs periodically on the BizTalkDTADb databases.  
  
-   **Excessive Disk I/O Latency** If the incoming rate of data into the MessageBox database is faster than which the system can process and move the data to the BizTalkDTADb database, backlog can build up in the MessageBox database. If the backlog continues to grow unabated, this is a very serious problem and system performance will degrade over time. One way to alleviate this problem is to install faster disks and/or upgrade the hardware to help ensure that the system is capable of recovering from any message backlogs experienced over time.  
  
## Plan for the Future  
 Even though all the best practices above are followed, over time the volume of tracking data moved to the BizTalkDTADb database will grow very large. It is important to implement a database maintenance plan to periodically archive tracking data so that the system can continue to perform optimally.  
  
 The amount of historical data that can be retained in the BizTalkDTADb database depends on the volume of messages pushed through the system. For systems that are not subjected to high stress and throughput this database will grow at a slower rate and it will be possible to retain more historical data in the BizTalkDTADb database.  
  
 It is recommended to retain minimal data in the BizTalkDTADb database so that runtime performance is not sacrificed.
