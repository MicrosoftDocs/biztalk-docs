---
description: "Learn more about: Best Practices for Backup and Restore"
title: "Best Practices for Backup and Restore"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: best-practice
---
# Best Practices for Backup and Restore
-   **Create a backup and restore plan**  
  
     Be sure your backup plan specifies:  
  
    -   The computer where backups will be stored  
  
    -   The programs that you will use to back up your system  
  
    -   The computers you want to back up  
  
    -   The schedule when backups will occur  
  
    -   The offsite location where you will archive backups  
  
-   **Keep a written record of all changes to your BizTalk Server system**  
  
     Be sure to write down all changes to your system, such as service packs, hotfixes, and QFEs that have been applied. This is crucial to getting your system restored as closely as possible to what existed before the hardware failure.  
  
-   **Implement the following measures to help prevent or minimize the effect of a disaster:**  
  
    -   Have your software and firmware updates available.  
  
    -   Have all software installation disks readily available. This includes both system software such as specialized drivers, and application software such as BizTalk Server.  
  
    -   Have a plan to monitor servers proactively. This is very important, since orchestration instances on a failed host may not be recovered by a second host for up to ten minutes.  
  
    -   Maintain hardware records.  
  
    -   Maintain software records.  
  
-   **Implement fault tolerance in your organization at the hardware or software level**  
  
     Implementing clusters and redundant array of independent disks (RAID) helps ensure that your system can survive a hardware failure.  
  
-   **Archive the backup media on a regular basis in a secure location**  
  
     Create a schedule for archiving your backup media on a regular basis and keep the archives in a secure, offsite location. This ensures that you have a backup available when you need it.  
  
-   **Verify the integrity of your backups and that they occur without error**  
  
     Monitor all of your backup jobs and ensure that they complete without any errors.  
  
-   **Keep identical spare hardware available**  
  
     Having identical spare hardware available ensures that you can quickly replace defective hardware to get up-and-running more quickly.  
  
-   **Document and test your recovery procedures**  
  
     Ideally, disaster recovery testing should be conducted before running your system in production. Having plans in place and performing prerelease testing will ensure that your IT staff can recover your BizTalk Server systems. This generally means that you must periodically attempt to retore the system backup to the actual hardware you will use  
  
-   **Train your IT staff on disaster recovery procedures**  
  
     Ensure that your IT staff is prepared to recover the system should the need arise.  
  
-   **Practice restoring from backup in a test environment**  
  
     Practice restoring your BizTalk Server system in a test environment to ensure that you can restore it to your production environment if a failure occurs.  
  
## See Also  
 [Backing Up and Restoring BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)
