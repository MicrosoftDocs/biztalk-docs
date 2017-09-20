---
title: "Monitoring and Reducing DTC Log File Disk I/O Contention | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8b968dd-216e-454f-9224-aaf92ffd363b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring and Reducing DTC Log File Disk I/O Contention
The Distributed Transaction Coordinator (DTC) log file can become a disk I/O bottleneck in transaction-intensive environments. This is especially true when using adapters that support transactions, such as SQL Server, MSMQ, or MQSeries, or in a multi-MessageBox environment. Transactional adapters use DTC transactions, and multi-MessageBox environments make extensive use of DTC transactions.  
  
## Monitoring Usage in Clustered and Non-Clustered Environments  
 To ensure that the DTC log file does not become a disk I/O bottleneck, you should monitor the disk I/O usage for the disk where the DTC log file resides on the SQL Server database server.  
  
 In an environment where SQL Server is clustered, this is not as much of a concern because the log file will already be on a shared drive, which will likely be a fast SAN drive with multiple spindles. You should nevertheless still monitor the disk I/O usage since it can become a bottleneck in non-clustered environments or when the DTC log file is on a shared disk with other disk-intensive files.  
  
## Troubleshooting DTC  
 For information about troubleshooting DTC, see "Troubleshooting Problems with MSDTC" in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help at [http://go.microsoft.com/fwlink/?LinkId=153237](http://go.microsoft.com/fwlink/?LinkId=153237).  
  
## See Also  
 [Checklist: Configuring Windows Server](../technical-guides/checklist-configuring-windows-server.md)