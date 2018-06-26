---
title: "Known Issues with the FTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e58f2db-9ec5-41fe-af02-9a7d60a217db
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with the FTP Adapter
This section contains information that may help you avoid errors.  
  
## Known Issues  
  
#### Data may be duplicated or lost when you receive data in BizTalk Server by using the FTP adapter  
  
##### Problem  
 Data is duplicated or lost when you receive data in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the FTP Adapter.  
  
##### Cause  
 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP adapter uses the FTP client protocol to poll the designated FTP server and retrieves data from the server "as is." The FTP adapter does not validate any data that it retrieves. The FTP adapter sends the retrieved document to the BizTalk Messaging Engine for processing and then it deletes the original document from the FTP server. If the FTP adapter retrieves a document from the FTP server that is still being written to by the host application, the retrieved document will be incomplete. If the FTP adapter retrieves an incomplete copy of the original document, data duplication or data loss may occur in the following scenarios:  
  
-   If the original document is still being written to the FTP server by the host application, the FTP adapter cannot delete the document and will retrieve another copy of the document at the next polling interval that is configured for the receive location. This behavior causes document duplication to occur.  
  
-   If the host application has finished writing the document to the FTP server, the document will be deleted. This behavior will cause data loss to occur.  
  
##### Resolution  
 To work around this behavior, use one of the following methods:  
  
- Configure the host application to write to a temporary folder on the same hard disk as the public FTP folder and to periodically move the contents of the temporary folder to the FTP folder. The temporary folder should be on the same hard disk as the public FTP folder to make sure that the move operation is atomic. An atomic operation is an operation that is functionally indivisible. If you write data to the public FTP folder by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] FTP adapter, you can do this by specifying a Temporary Folder property in the FTP Transport Properties dialog box when you configure a send port. If you specify a Temporary Folder property, make sure that this folder is on the same physical disk as the public FTP folder.  
  
- Configure the FTP receive location to operate within a service window when the host application is not writing data to the FTP server. You can specify the service window when you configure the receive location properties.  
  
#### FTP Adapter does not support revocation checks on the server certificates  
  
##### Problem  
 The FTP adapter in BizTalk Server is enhanced to support secure file transfer to and from an FTPS server using SSL/TLS. The Certificate Revocation List (CRL) contains a list of certificates that have been revoked and are no longer valid. The FTP adapter does not consult the CRL for authenticating the server certificate.  
  
##### Cause  
 By design, the FTP adapter does not consult the CRL before accepting a server certificate.  
  
##### Resolution  
 No action is required; this behavior is by design.  
  
#### FTP Adapter downloads files larger than Max File Size  
  
##### Problem  
 The FTP receive adapter downloads files whose size is larger than the specified Max File Size property from the following FTP servers:  
  
-   AIX  
  
-   MVS  
  
-   AS400  
  
-   GXS  
  
##### Cause  
 By design, the FTP adapter does not respect the maximum file size when downloading files from these FTP servers.  
  
##### Resolution  
 No action is required; this behavior is by design.  
  
## See Also  
 [How to Configure an FTP Receive Location](http://msdn.microsoft.com/library/1d8fde35-f787-4a5e-a8bd-8c418d0f75c3)   
 [Troubleshooting the FTP Adapter](../core/troubleshooting-the-ftp-adapter.md)