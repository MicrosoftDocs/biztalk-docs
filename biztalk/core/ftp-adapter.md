---
title: "FTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FTP adapters"
ms.assetid: 878dc0b0-d1d8-405a-a697-654dd18ba08e
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# FTP Adapter
The FTP adapter exchanges data between an FTP server and Microsoft BizTalk Server, and allows for the integration of vital data stored on a variety of platforms with line-of-business applications. The adapter can connect to the FTP server via SOCKS4 or SOCKS5 proxy server.  
  
 The FTP adapter can transfer a large number of files from an FTP server to BizTalk Server. It can also transfer files as part of an orchestration.  
  
 The FTP adapter consists of two adapters — a receive adapter and a send adapter.  

This section describes the FTP receive and send adapters, as well as security and best-practice information.  
  
 ## Receive adapter  
  
 The FTP receive adapter enables you to move data from an FTP server to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Key features include:  
  
- Pulling files from the FTP server on demand  
  
- Running polls based on a configurable schedule  
  
- Polling the FTP server and sending data directly to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- Specifying the FTP server as an IP address, port, password, and host name  
  
- Guaranteed file delivery  
  
   The FTP receive adapter also works with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and BizTalk Explorer to configure and administer each receive function, which is composed of the following configuration items:  
  
- Poll interval to run an FTP command (for example, 60 minutes)  
  
- Information with which to route the document to a specific BizTalk send port or receive location  
  
> [!NOTE]
>  The FTP receive adapter does not support receiving files from a partitioned data set.  
  
## Send adapter  
  
 The FTP send adapter enables you to move data from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to an FTP server. Key features include:  
  
-   Ability to run sends on demand  
  
-   Guaranteed delivery  
  
## Supported platforms  
Access information stored in an FTP server on any of the following platforms:  

- [!INCLUDE[btsWinSvrNoVersion_md](../includes/btswinsvrnoversion-md.md)] 2016

- [!INCLUDE[btsWinSrv2k12_md](../includes/btswinsrv2k12-md.md)] R2
  
- [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]  
  
- [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]  
  
- [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 2008  
  
- [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]  
  
- [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 2000 Service Pack 3 (SP3) and later  
  
- Sun Solaris 9.0  
  
- HP-UX  
  
- LINUX (Redhat 7.x)  
  
- IBM z/OS v1.9 (MVS)  
  
- IBM O/S 390 running MVS  
  
- AS/400 OS/400 V5R1  
  
- i5/OS V5R4 (AS400)  
  
- i5/OS V6R1 (AS400)  
  
- GXS ICS  
  
- AIX  
  
  All services packs are supported, unless the service pack is specifically listed.  
  
## In This Section  
  
[Best practices and recommendations for the FTP Adapter](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)  

[Configuring the FTP adapter](../core/configuring-the-ftp-adapter.md)  

[FTP Adapter Property Schema and Properties](../core/ftp-adapter-property-schema-and-properties.md)