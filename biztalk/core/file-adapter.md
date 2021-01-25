---
description: "Learn more about: File Adapter"
title: "File Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "File adapters"
ms.assetid: e4f6e94b-89b8-42ba-a4c2-a629f1107bb1
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Adapter
The File adapter transfers files into and out of Microsoft BizTalk Server. The File adapter consists of two adapters — a receive adapter and a send adapter.  
  
 This section discusses the workflow and batching support for both the File receive adapter and the File send adapter.  
 
## File receive adapter  
  
Use the File receive adapter to read messages from files, and submit them to the server. The receive adapter reads the file, and creates a BizTalk Message object, so that BizTalk Server can process the message. While reading from the file, the adapter locks the file to ensure that no modifications can be made to the file content.  
  
> [!NOTE] 
> The File receive adapter does not pick up read-only files or system files.  
  
 The File receive adapter reads the messages from files on local file systems or on network shares. When the specified location on a network share is unavailable due to network problems, the receive adapter retries the read operation (the number of retries is configurable in the BizTalk Server Administration console). After the message has been read and successfully accepted by the BizTalk Messaging Engine, the receive adapter deletes the file from the file system or network share. If the message was read but the pipeline did not successfully process the message, the adapter puts the message in the suspended queue and then deletes the file from the file system or network share. If the File receive adapter cannot submit or suspend the message to the MessageBox database, it does not delete the original file from the file system or network share.  
  
 You can also configure the File receive adapter to rename files when processing them. You should rename files to ensure that the receive adapter does not generate duplicate messages if the receive location is shut down and restarted. This is a configurable option for File receive locations. By default, renaming is disabled. When renaming is enabled, the File receive adapter appends the extension .BTS-WIP to the file. The receive adapter then reads the messages from the renamed file in the receive location and submits it to the server. After the receive adapter has successfully submitted a file, the receive adapter deletes the renamed file from the file system or network share. If a message has been read but failed processing in the pipeline, the receive adapter places the message in the MessageBox database suspended queue, and deletes the renamed file from the network share.  
  
> [!NOTE] 
> Renaming files has no impact on performance.  
  
 If the File receive adapter successfully reads the message but did not successfully store the message in the MessageBox database, the renamed file reverts to its original name, without the .BTS-WIP extension. Note that the receive adapter does not read files with the extension .BTS-WIP if the renaming option is turned on.  
  
#### Using file change notifications and polling
  
 The File receive adapter relies on Windows File Change Notifications to determine when to pick up a file from the specified directory or share. If the File receive adapter receives a Windows File Change Notification before the file has been completely written to the specified directory or share then the file will be locked and the File receive adapter will not retrieve the file. In this scenario, the File receive adapter will actively poll the specified directory or share at the **Polling interval (ms)** specified on the **Advanced settings** dialog box available when configuring a File receive location. When the File receive adapter polls a directory or share it retrieves unlocked files from the share and submits the files to the MessageBox database.  
  
> [!NOTE]
>  The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] File adapter has only been tested on, and is supported on, the NTFS file system.  
  
 The following Windows File Change Notifications will cause the File receive adapter to pick up a file from the specified location:  
  
 `FILE_NOTIFY_CHANGE_ATTRIBUTES`
  
 Any attribute change in the watched directory or subtree causes a change notification wait operation to return.  
  
 `FILE_NOTIFY_CHANGE_FILE_NAME`  
  
 Any file name change in the watched directory or subtree causes a change notification wait operation to return. Changes include renaming, creating, or deleting a file name.  
  
 `FILE_NOTIFY_CHANGE_SIZE`  
  
 Any file-size change in the watched directory or subtree causes a change notification wait operation to return. The operating system detects a change in file size only when the file is written to the disk. For operating systems that use extensive caching, detection occurs only when the cache is sufficiently flushed.  
  
 `FILE_NOTIFY_CHANGE_LAST_WRITE`  
  
 Any change to the last write-time of files in the watched directory or subtree causes a change notification wait operation to return. The operating system detects a change to the last write-time only when the file is written to the disk. For operating systems that use extensive caching, detection occurs only when the cache is sufficiently flushed.  
  
 For more information about the **FindFirstChangeNotification** function see [https://msdn.microsoft.com/library/windows/desktop/aa364417(v=vs.85).aspx](https://msdn.microsoft.com/library/windows/desktop/aa364417(v=vs.85).aspx).  
  
### File Receive Adapter Batching Support
  
 The File receive adapter submits messages to the server in batches. The File receive adapter starts by building a single batch per receive location by collecting all the readable files available in the receive location. Batches are submitted to the MessageBox database by the receive adapter when all the available files have been collected or when the amount of files collected exceeds the maximum batch size.  
  
 After all the messages within the batch have been successfully read and submitted into the MessageBox database, the File receive adapter deletes the corresponding files from the receive location. If some of the messages within the batch failed processing, the File receive adapter suspends them and deletes the corresponding files from the receive location. If some or all of the messages fail to be stored in the MessageBox database, the entire batch operation is rolled back and all corresponding files are left unchanged in the receive location.  
  
## File Send Adapter
  
 The File send adapter transmits messages from the MessageBox database to a specified destination address (URL). You define the URL, which is a file path and file name, by using wildcard characters related to the message context properties. The File send adapter resolves the wildcard characters to the actual file name before writing the message to the file.  
  
 When writing a message to a file, the File send adapter gets the message content from the body part of the BizTalk Message object. The File send adapter ignores other message parts in the BizTalk Message object. After the File adapter writes the message to a file, it deletes the message from the MessageBox database. The File adapter writes files to the file system either directly or by using the file system cache, which can improve performance, particularly for large files.  
  
### File Send Adapter Batching Support
  
 The File send adapter gets batches of messages from the MessageBox database and writes them to files in destination locations on the file system or the network share. The size of File send adapter batches is not configurable and is preset to 20. If BizTalk Server fails to write some of the messages within a batch to files, the system resubmits those messages to the MessageBox database for retry processing. You can configure the retry interval and retry count by using the BizTalk Server Administration console.  
  
 
## In this section  
  
-   [Configure the File adapter](../core/configure-the-file-adapter.md) 
  
-   [Restrictions when configuring the File adapter](../core/restrictions-when-configuring-the-file-adapter.md)  
