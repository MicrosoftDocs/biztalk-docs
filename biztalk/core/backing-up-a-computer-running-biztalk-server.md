---
description: "Learn more about: Backing Up a Computer Running BizTalk Server"
title: "Backing Up a Computer Running BizTalk Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Backing Up a Computer Running BizTalk Server
If a computer running BizTalk Server suffers an irrecoverable hardware failure, then you must replace that computer with an identical one. You should set up the replacement computer with the base platform software, software prerequisites, BizTalk Server components, and identical configuration settings. These configuration settings may consist of the appropriate registry entries, files, folders, and related Windows services necessary for the correct operation of your BizTalk applications.  
  
 In addition to backing up the BizTalk Server databases, you should back up the following BizTalk Server components to ensure that you can recover BizTalk Server after a hardware failure:  
  
-   BizTalk Server configuration  
  
-   Enterprise Single Sign-On (SSO) master secret  
  
-   Business Activity Monitoring (BAM) portal (not required unless you're using BAM)  
  
-   BizTalk applications  
  
## In This Section  
  
-   [How to Back Up The BizTalk Server Configuration](../core/how-to-back-up-the-biztalk-server-configuration.md)  
  
-   [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md)  
  
-   [How to Back Up the BAM Portal](../core/how-to-back-up-the-bam-portal.md)  
  
-   [Backing Up BizTalk Server Applications](../core/backing-up-biztalk-server-applications.md)
