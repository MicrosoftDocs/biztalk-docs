---
title: "File System Choices and Security1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e802d7e6-cec7-4110-98d4-f66e5a2c4059
caps.latest.revision: 4
---
# File System Choices and Security
One of the keys to controlling security on Host Integration Server computers is the configuration file. To maintain good security with this file, be sure to install the Host Integration Server server software on an NTFS (NT File System) partition. With NTFS, you can assign permissions on a file-by-file basis. With the FAT (File Allocation Table) file system or HPFS (High Performance File System), this is not possible. Installing Host Integration Server software on an NTFS partition is especially important for the primary server because this computer contains the master copy of the configuration file used by all Host Integration Server computers in the subdomain.  
  
 If you must install Host Integration Server on a non-NTFS partition, you can limit a users ability to view or change a Host Integration Server configuration file through the Host Integration Server SNA Manager, but you will not be able to set file permissions on the configuration file itself.  
  
 In addition, if you choose to install the software for one or more servers on a FAT or HPFS partition, you can set appropriate Read and Change permissions on the share, which gives servers access to the configuration file. (This is unnecessary for Host Integration Server software installed on an NTFS partition, because file permissions established through the Host Integration Server SNA Manager place tighter control on the configuration file than can be established by controlling the share.)  
  
## See Also  
 [Understanding Windows Security](../core/understanding-windows-security2.md)