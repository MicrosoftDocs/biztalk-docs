---
description: "Learn about security in the Microsoft OLE DB Provider for DB2 (Data Provider) that connects Microsoft SQL Server database applications to remote IBM DB2 relational database management servers."
title: "Security2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7afe4c2a-c839-4885-afa0-55c7373f7c9c
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Security with the Microsoft OLE DB Provider for DB2 (Data Provider)

The Microsoft OLE DB Provider for DB2 (Data Provider) connects Microsoft SQL Server database applications to remote IBM DB2 relational database management servers, for on-line transaction processing, analysis and reporting. The Data Provider functions as a DB2 application requester client supporting the standard distributed relational database architecture (DRDA) protocols and formats that are compatible with IBM DB2 server products functioning as DB2 application servers.  
  
The Data Provider enables interoperability between DB2 client applications and DB2 server databases by issuing structured query language statements. These include data definition language statements for administration and data manipulation management statements for read and write operations. The Data Provider connects the DB2 client applications to the DB2 server databases across a transmission control protocol over internet protocol (TCP/IP) network that uses the optional security features described in this topic.  
  
## User Account

The Data Provider, Data Access Tool and Data Links, run in the context of a user account for the SQL Server 2014 OLE DB consumer program, such as the SQL Server Data Tools (SSDT) or the SQL Server Management Studio.  
  
## Folder Access Control List

The user account requires the Folder Access Control List settings to for these folders.  
  
|File Folder|Modify|Read & execute|List folder contents|Read|Write|Special permissions|  
|-----------------|------------|--------------------|--------------------------|----------|-----------|-------------------------|  
|Program Files\Microsoft OLE DB Provider for DB2||Allow|Allow|Allow|||  
|Program Files\Microsoft OLE DB Provider for DB2\system||Allow|Allow|Allow|||  
|Program Files\Microsoft OLE DB Provider for DB2\ SysWOW64||Allow|Allow|Allow|||  
|Program Files\Microsoft OLE DB Provider for DB2\traces||Allow|Allow|Allow|Allow||  
|Documents\Host Integration Server\Data Sources||Allow|Allow|Allow|Allow||
