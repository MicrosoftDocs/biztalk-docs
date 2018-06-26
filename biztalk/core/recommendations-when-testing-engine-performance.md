---
title: "Recommendations When Testing Engine Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maximum sustainable throughput (MST), best practices"
ms.assetid: 0aa9d833-0e7d-4347-a6ca-8d658749b4f2
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Recommendations When Testing Engine Performance
The following guidelines should be followed when testing BizTalk engine performance:  
  
 **Know your load behavior profile** As the three load tests have illustrated, it is critical to know the profile of your load in terms of messages processed over time.  The better this is understood, the more accurately you can test and adjust your system capacity. If all you know is your peak throughput requirement, then the most conservative approach would be to size your system so that your maximum sustainable throughput is the same or higher than your peak load. However, if you know that you have predictable peaks and valleys in your load, you can better optimize your system to recover between peaks, resulting in a smaller, less expensive overall deployment.  
  
 **Test performance early** Avoid falling into the trap of investing significant effort in designing and testing the functionality of your solution, but waiting until the last minute to test performance on production hardware. Run performance tests on your system that simulate the expected load profile as early as you possibly can in your development cycle. If you have to change anything in your design or architecture to achieve your goals knowing this early will give you time to adjust and test again.  
  
 **Emulate your expected load profile when testing performance** There are two primary components to this:  
  
1. Emulate the load profile over time.  
  
2. Run the test long enough to evaluate if it is sustainable.  
  
   If, as is commonly the case, your cycles are daily in nature you should plan to run performance tests for at least one day to validate sustainability. The longer that you run the tests, the better.  
  
   **Emulate the production configuration** For example, the number and type of ports, the host and host instance configuration, database configuration, and adapter setup. Don’t assume that configuration changes will not significantly impact performance.  
  
   **Use real messages** Message sizes and message complexity affect performance, so be sure and test with the same message schemas and instances that you plan to see in production.  
  
   **Emulate your normal operations during performance tests** Though the load tests did not include them, standard operations activities such as periodic database queries, backups, and purging will affect your sustainable throughput, so make sure you are performing these tasks during your performance and capacity test runs. This includes both DTA and BAM tracking, if you plan to use them in production.  
  
   **The speed of the I/O subsystem for the MessageBox is a key success factor** The load tests that were performed made use of a fast Storage Area Network for the MessageBox database files that is dedicated to this build-out. Even in this case, the cleanup jobs were able to drive the idle time to near zero for the SQL data file. The I/O subsystem is frequently a bottleneck in production systems. A common strategy to optimize SQL I/O is to place the database data file(s) and log file(s) on separate physical drives, if possible.  
  
   **Make sure the SQL Agent is running on all MessageBox servers** Clearly, the cleanup jobs will never run if the SQL Agent is not running, so make sure these are running.  
  
   **Spool depth is a key indicator** Regardless of other indicators, this measure will give you a quick and easy way to assess if your system is being overdriven or not.