---
description: "Learn more about: File adapter property schema and properties"
title: "File adapter property schema and properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# File adapter property schema and properties
The following table contains the properties in the File adapter property schema.  
  
 **Namespace:** `http://schemas.microsoft.com/BizTalk/2003/file-properties`
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|**CopyMode**|xs:unsignedInt|Defines the copy mode to use when writing a message to a file. Valid values are:<br /><br /> **Append (0).** The File send handler opens a file if it exists and appends a message to the end of the file. If the file does not exist, the File send handler creates a new file.<br /><br /> **Create new (1).** If a file does not exist, the File send handler creates a new file and writes to it. If the file already exists, the File send handler reports an error and then follows common adapter retry logic for send ports. This is a default copy mode for the File send handler.<br /><br /> **Overwrite (2).** The File send handler opens a file if it exists and overwrites its content. If the file does not exist, the File send handler creates a new file.|  
|**AllowCacheOnWrite**|xs:Boolean|Defines whether the File adapter uses file system caching when writing messages to a file.|  
|**ReceivedFileName**|xs:string|Defines the full name of the file from which the File adapter reads the message.|  
|**FileCreationTime**|xs:datetime|Defines the time that the file was written to the folder that is monitored by the File receive adapter.|  
|**Username**|xs:string|Defines the user name for the account used when specifying alternative credentials to access a network share.|  
|**Password**|xs:string|Defines the password for the account used when specifying alternative credentials to access a network share.|  
|**TargetFileName**|xs:string||
|**UseTempFileOnWrite**|xs:boolean||
  
## See Also  
 [Configuring the File Adapter](../core/configure-the-file-adapter.md)
