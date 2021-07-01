---
description: "Learn more about: File Adapter Configuration Properties"
title: "File Adapter Configuration Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "File adapters, code sample"
  - "receive locations, adapters"
  - "File adapters, send ports"
  - "File adapters, receive locations"
  - "File adapters, properties"
  - "send ports, adapters"
ms.assetid: 53f4fd17-95b9-4861-b433-772b619e90c7
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Adapter Configuration Properties
The following table lists the configuration properties that you can set for a File adapter receive location:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|RemoveReceivedFileRetryCount|VT_UI4|Specify the number of times that the File adapter will attempt to delete a file that it has read and submitted to BizTalk Server.|Valid values are from 0 to 100.|The default value is 5.|  
|RemoveReceivedFileMaxInterval|VT_UI4|Specify the initial interval in milliseconds that the File adapter waits before attempting to delete a file that it has read and submitted to BizTalk Server.|Valid values are from 1 to 1000.|The default value is 10.|  
|FileMask|VT_BSTR|Specify the mask for the files.|None|The default value is *.xml.|  
|BatchSizeInBytes|VT_UI4|Specify the maximum total bytes for a batch of files sent to the BizTalk MessageBox.|Valid values are from 1024 to 104857600.|The default value is 102400.|  
|PollingInterval|VT_UI4|Specify the interval in milliseconds that the File adapter will poll the specified location for new files.|Valid values are from 1000 to 3600000.|Set to 1 to disable polling.|  
|BatchSize|VT_UI4|Specify the maximum number of messages to be submitted in a batch.|Valid values are from 1 to 256.|The default value is 20.|  
|FileNetFailRetryInt|VT_UI4|Specify the retry interval time (in minutes) between attempts to access the receive location on the network share if it is temporarily unavailable.|Valid values are from 0 to 4294967295.|The default value is 5.|  
|RemoveReceivedFileDelay|VT_UI4|Specify the initial interval in milliseconds that the File adapter waits before attempting to delete a file that it has read and submitted to BizTalk Server.|This interval will double after each retry interval up to the specified maximum retry interval value.<br /><br /> Valid values are from 1 to 1000.|The default value is 10.|  
|RenameReceivedFiles|VT_BOOL|Specify whether to rename files before picking them up for processing.|Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0.|  
|FileNetFailRetryCount|VT_UI4|Specify the number of attempts to access the receive location on a network share if it is temporarily unavailable.|Valid values are from 0 to 4294967295.|The default value is 5.|  
  
 The following code shows the format of the XML string you use to set the properties:  
  
```  
<CustomProps>  
<RemoveReceivedFileRetryCount vt="19">5</RemoveReceivedFileRetryCount>  
<RemoveReceivedFileMaxInterval vt="19">300000</RemoveReceivedFileMaxInterval>  
<FileMask vt="8">*.xml</FileMask>  
<BatchSizeInBytes vt="19">102400</BatchSizeInBytes>  
<PollingInterval vt="19">60000</PollingInterval>  
<BatchSize vt="19">20</BatchSize>  
<FileNetFailRetryInt vt="19">5</FileNetFailRetryInt>  
<RemoveReceivedFileDelay vt="19">10</RemoveReceivedFileDelay>  
<RenameReceivedFiles vt="11">0</RenameReceivedFiles>  
<FileNetFailRetryCount vt="19">5</FileNetFailRetryCount>  
</CustomProps>  
```  
  
 The following table lists the configuration properties that you can set for a File adapter send port:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|Username|VT_BSTR|Specify alternative credentials when the host instance for the File adapter does not have the necessary rights to a network share.|None|Specify the username in the format \<domain\>\username.|  
|UseTempFileOnWrite|VT_BOOL|Specifies to use a temporary file when writing to the target folder. Once file is finished writing it is renamed to the value specified for the Filename property.|This property can only be set to -1 (true) if the CopyMode property is set to a value of 2 (Create new).<br /><br /> Valid values are:<br /><br /> -   -1 (true)<br />-   0 (false)|The default value is 0 (false).|  
|CopyMode|VT_UI4|Define the copy mode to use when writing a message to a file|Valid values are:<br /><br /> -   0 (Append)<br />-   1 (Overwrite)<br />-   2 (Create new)|The default value is 2 (Create new).|  
|FileName|VT_BSTR|Specify the name of the file where the file send handler writes the message.|For information about restrictions on this property, see [Restrictions when configuring the File adapter](restrictions-when-configuring-the-file-adapter.md).|The default value is %MessageID%.xml.|  
|AllowCacheOnWrite|VT_BOOL|Specify whether to use file system caching when writing a message to a file.|Valid values are:<br /><br /> -   0 (do not use caching)<br />-   -1 (use caching)|The default value is 0 (do not use caching).|  
|Password|VT_NULL|Specify the password used in conjunction with the Username property when the host instance for the File adapter does not have the necessary rights to a network share.|This value is always set to null when exporting a binding file. This field must be manually populated with the password before importing the binding file into the target BizTalk Server configuration.|None|  
  
 The following code shows the format of the XML string you use to set the properties:  
  
```xml
<CustomProps>  
<Username vt="8">Domainname\User</Username>  
<UseTempFileOnWrite vt="11">-1</UseTempFileOnWrite>  
<CopyMode vt="19">1</CopyMode>  
<FileName vt="8">%MessageID%.xml</FileName>  
<AllowCacheOnWrite vt="11">-1</AllowCacheOnWrite>  
<Password vt="1" />  
</CustomProps>  
```
