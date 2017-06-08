---
title: "File adapter property schema and properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [File adapters], properties"
  - "schemas, File adapters"
  - "File adapters, schemas"
  - "Password property [File adapters]"
  - "ReceivedFileName property [File adapters]"
  - "configuring [File adapters], schemas"
  - "CopyMode property [File adapters]"
  - "AllowCacheOnWrite property [File adapters]"
  - "FileCreationTime property [File adapters]"
  - "UserName property, File adapters"
  - "File adapters, properties"
  - "UserName property"
ms.assetid: c5ae5339-67bf-4fde-a721-5b1aa3b9caca
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File adapter property schema and properties
The following table contains the properties in the File adapter property schema.  
  
 **Namespace:** http://schemas.microsoft.com/BizTalk/2003/file-properties  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|**CopyMode**|xs:unsignedInt|Defines the copy mode to use when writing a message to a file. Valid values are:<br /><br /> **Append (0).** The File send handler opens a file if it exists and appends a message to the end of the file. If the file does not exist, the File send handler creates a new file.<br /><br /> **Create new (1).** If a file does not exist, the File send handler creates a new file and writes to it. If the file already exists, the File send handler reports an error and then follows common adapter retry logic for send ports. This is a default copy mode for the File send handler.<br /><br /> **Overwrite (2).** The File send handler opens a file if it exists and overwrites its content. If the file does not exist, the File send handler creates a new file.|  
|**AllowCacheOnWrite**|xs:Boolean|Defines whether the File adapter uses file system caching when writing messages to a file.|  
|**ReceivedFileName**|xs:string|Defines the full name of the file from which the File adapter reads the message.|  
|**FileCreationTime**|xs:datetime|Defines the time that the file was written to the folder that is monitored by the File receive adapter.|  
|**Username**|xs:string|Defines the user name for the account used when specifying alternative credentials to access a network share.|  
|**Password**|xs:string|Defines the password for the account used when specifying alternative credentials to access a network share.|  
  
## See Also  
 [Configuring the File Adapter](../core/configure-the-file-adapter.md)