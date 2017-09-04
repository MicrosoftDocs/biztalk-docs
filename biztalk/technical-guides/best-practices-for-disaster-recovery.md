---
title: "Best Practices for Disaster Recovery | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afbb0a57-0d31-4a2f-847c-02b40361c0ed
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Disaster Recovery
For information about best practices for disaster recovery for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], see [Best Practices for Backup and Restore](http://go.microsoft.com/fwlink/?LinkId=151391) (http://go.microsoft.com/fwlink/?LinkId=151391) in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help.  
  
 **Create a backup and restore plan**  
  
-   Be sure your backup plan specifies:  
  
    -   The computer where backups will be stored  
  
    -   The programs that you will use to back up your system  
  
    -   The computers you want to back up  
  
    -   The schedule when backups will occur  
  
    -   The offsite location where you will archive backups  
  
 **Keep a written record of all changes to your BizTalk Server system**  
  
-   Be sure to write down all changes to your system, such as service packs, hotfixes, and QFEs that have been applied. This is crucial to getting your system restored as closely as possible to what existed before the hardware failure.  
  
 **Implement the following measures to help prevent or minimize the effect of a disaster**  
  
-   Have your software and firmware updates available.  
  
-   Have all software disks readily available.  
  
-   Have a plan to monitor servers proactively. This is very important since orchestration instances on a failed host may not be recovered by a second host for up to 10 minutes.  
  
-   Maintain hardware records.  
  
-   Maintain software records.  
  
 **Implement fault tolerance in your organization at the hardware or software level**  
  
-   Implementing clusters and redundant array of independent disks (RAID) helps ensure that your system can survive a hardware failure.  
  
 **Archive the backup media on a regular basis in a secure location**  
  
-   Create a schedule for archiving your backup media on a regular basis and keep the archives in a secure, offsite location. This ensures that you have a backup available when you need it.  
  
 **Verify the integrity of your backups and that they occur without error**  
  
-   Monitor all of your backup jobs and ensure that they complete without any errors.  
  
 **Keep identical spare hardware available**  
  
-   Having identical spare hardware available ensures that you can quickly replace defective hardware to get up and running more quickly.  
  
 **Document and test your recovery procedures**  
  
-   Disaster recovery testing should be conducted before ever running your system in production. Having plans in place and performing prerelease testing will ensure that your IT staff can recover your BizTalk Server systems.  
  
 **Train your IT staff on disaster recovery procedures**  
  
-   Ensure that your IT staff is prepared to recover the system should the need arise.  
  
 **Practice restoring from a backup in a test environment**  
  
-   Practice restoring your BizTalk Server system in a test environment to ensure that you can restore it to your production environment if a failure occurs.  
  
## See Also  
 [Disaster Recovery](../technical-guides/disaster-recovery.md)