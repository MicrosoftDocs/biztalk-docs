---
description: "Learn how to avoid disk contention in a BizTalk Server system."
title: "How to Avoid Disk Contention1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b4f8e10-16b0-45f9-8787-da16266da980
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Avoid Disk Contention

BizTalk Server is designed as a persistent system whereby, for high throughput scenarios, the MessageBox can experience severe contention. This contention can be aggravated by slow disks. If the disks are slow (low % Disk Idle Time), this can cause SQL to hold onto locks longer (high Lock Wait Time and high Lock Timeouts) which can cause the MessageBox tables (Spool and Application Queues) to grow, causing database bloat and throttling ultimately resulting in lower overall sustainable throughput.  
  
To avoid disk contention, it is recommended that you do the following:  
  
- Use of high speed (multiple spindles) disks.  
  
- If possible, deploy the databases on a high speed SAN. If multiple databases are sharing the same disks it is recommended to configure them on separate dedicated disks. In addition it is recommended to separate the MDF and LDF files for the MessageBox database onto separate disks.  
  
- If SQL is starved for CPU, consider separating the MessageBox database onto a dedicated server that is separate from the Tracking databases.  
  
- After setting up a dedicated server for the MessageBox database, consider scaling up by upgrading the CPU’s and/or adding more CPU’s. Monitor the local drive on the SQL-Server as the MSDTC logs are saved on the local drive (C:\WINDOWS\system32\Msdtc).  
  
- If there is contention on the local drive due to the PageFile or MSDTC log, try moving the PageFile and/or the MSDTC log to a separate drive.
