---
description: "Learn more about: Known Issues with the File Adapter"
title: "Known Issues with the File Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aaf448c-0035-4648-910b-ae2f15106342
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with the File Adapter
This section contains information that may help you avoid errors.  
  
## A File Receive Location is Disabled  
  
### Problem  
 A File receive location becomes disabled.  
  
### Cause  
 The File receive adapter disables the receive location if any of the following occur:  
  
-   The File receive adapter cannot access the receive location on the file system or network share because the specified path does not exist. For a network share, the File receive adapter disables the receive location after all retry attempts have been exhausted.  
  
-   The File receive adapter cannot access the receive location on the file system or network share because the account used by the associated host instance does not have read-write permission for that location. For a network share, the File receive adapter disables the receive location after all retry attempts have been exhausted.  
  
-   Files with names longer than 256 characters are encountered in the receive location.  
  
### Resolution  
  
-   Ensure that the specified path or share exists.  
  
-   Ensure that the account used as the **Logon:** account for the File receive handler host instance has read and write permissions to the specified receive location.  
  
-   Ensure that files written to the folder monitored by the File receive adapter do not have file names exceeding 256 characters.  
  
## Files Are Not Being Read from the Specified Receive Location  
  
### Problem  
 The File receive adapter does not read a file from the specified receive location. When the File receive adapter encounters such a file, it logs an error in the event log and leaves the file in the receive location.  
  
### Cause  
 The File receive adapter does not read a file from the receive location if any of the following conditions are true:  
  
-   The file is read-only.  
  
-   The file has a system attribute.  
  
-   The File receive adapter does not have permissions to read and write to the file.  
  
-   Files with names longer than 256 characters are encountered in the receive location.  
  
### Resolution  
  
-   Ensure that the files in the specified receive location are not marked as "read only".  
  
-   Ensure that the files in the specified receive location are not marked with a system attribute.  
  
-   Ensure that the account used as the **Logon:** account for the File receive handler host instance has read and write permissions to the specified receive location.  
  
-   Ensure that files written to the folder monitored by the File receive adapter do not have file names exceeding 256 characters.  
  
## Messages Are Not Being Sent by the File Send Adapter  
  
### Problem  
 The File send adapter fails to send a message to the specified directory or file share.  
  
 If a message fails to be written to the specified directory or file share, an error is written to the Event log of the BizTalk server computer and the following sequence of events occurs:  
  
1.  The File send adapter will retry the write operation.  
  
2.  The File adapter will attempt to deliver the file using the backup transport (if configured).  
  
3.  The message will be written to the suspended queue.  
  
### Cause  
  
-   The File send adapter cannot access the directory that files are sent from on the file system or network share because the specified path does not exist.  
  
-   The File send adapter cannot write to a file in the destination location on the file system or network share because the associated host instance does not have write permissions for that file or for that location.  
  
-   The File send adapter cannot write to the file specified because it is read-only or is marked with the **system** file attribute.  
  
### Resolution  
  
-   Ensure that the specified path or share exists.  
  
-   Ensure that the account used as the **Logon:** account for the File send handler host instance has read and write permissions to the specified directory or file share.  
  
-   Ensure that existing files in the specified directory or file share are not marked with the system attribute.  
  
## Sending a file using the File adapter is very slow  
  
### Problem  
 Performance of the File send adapter is slower when the **Allow cache on write** property is set to **False**. The **Allow cache on write** property is set to **False** by default.  
  
### Cause  
 Setting the **Allow cache on write** property to **False** can reduce performance as this setting disallows the use of in-memory caching of files by the operating system.  
  
### Resolution  
 To increase performance of the File send adapter change the **Allow cache on write** property to **True** (check the box). For more information about the **Allow cache on write** property, see [Configure a File Send Port](configure-the-file-adapter.md).  
  
> [!NOTE]
>  Setting the **Allow cache on write** property to **True** increases the possibility of data loss in the event that the operating system experiences a failure. In this scenario, any data that is stored in the in-memory file cache will be lost.  
  
## Zero byte files received by the File adapter are deleted  
  
### Problem  
 If an empty (zero byte) file is picked up by the File receive adapter, the file is deleted and a warning similar to the following is written to the application log of the BizTalk server:  
  
```  
Event Type:Warning  
Event Source:BizTalk Server 2009  
Event Category:BizTalk Server 2009   
Event ID:7182  
Date:8/30/2006  
Time:1:32:32 PM  
User:N/A  
Computer:BIZTALKSERVER  
Description:  
The FILE receive adapter deleted the empty file "C:\filesource\emptyfile.xml.BTS-WIP" without performing any processing.  
```  
  
### Cause  
 The File receive adapter deletes zero byte files by design.  
  
### Resolution  
 No action is required, this behavior is by design.
