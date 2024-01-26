---
description: "Learn more about: Distributed Relational Database Architecture"
title: "Distributed Relational Database Architecture1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Distributed Relational Database Architecture
The DRDA Service supports DRDA Version 5.  
  
## DRDA Manager Levels  
 The DRDA Service supports the below-listed DRDA Manager Levels.  
  
|Manager|Min|Max|Description|  
|-------------|---------|---------|-----------------|  
|AGENT|3|7|Agent Manager represents application requester|  
|CMNAPPC|NA|NA|SNA APPC LU6.2 conversational communications manager|  
|CMNSYNCPT|4|4|SNA APPC LU6.2 conversational sync point communications manager|  
|CMNTCPIP|5|8|TCP/IP communications manager|  
|RDB|3|8|Relational database|  
|RSYNCMGR|5|5|Resynchronization manager|  
|SECMGR|5|8|Security manager|  
|SQLAM|3|8|SQL application manager|  
|SYNCPTMGR|5|7|Sync point manager|  
|XAMGR|NA|NA|XA manager|  
  
## DRDA Package Bind Code Points  
 DRDA Service supports a limited set of DRDA BNDOPT (Bind Options).  
  
|DRDA Code Point|Static SQL XML Format V90|DRDA Service|  
|---------------------|-------------------------------|------------------|  
|BNDCHKEXS|Bind Existence Checking|Not supported|  
|BNDCRTCTL|Bind Package Creation Control|Supported|  
|BNDEXPOPT|Bind Explain Option|Not supported|  
|DECPRC|Decimal Precision|Not supported|  
|DFTRDBCOL|Default RDB Collection ID|Not supported|  
|DGRIOPRL|Degree of I/O Parallelism|Not supported|  
|PKGATHOPT|Package Authorization Option|Not supported|  
|PKGATHRUL|Package Authorization Rules|Not supported|  
|PKGDFTCC|Package Default CCSIDs for a Column|Not supported|  
|PKGDFTCST|Package Default Character Subtype|Not supported|  
|PKGISOLVL|Package Isolation Level|Not supported|  
|PKGNAMCT|Package Name and Consistency Token|Supported|  
|PKGOWNID|Package Owner Identifier|Not supported|  
|PKGRPLOPT|Package Replacement Option|Supported|  
|PKGRPLVRS|Replaced Package Version Name|Supported|  
|PRPSTTKP|Prepared Statement Keep|Not supported|  
|QRYBLKCTL|Query Block Protocol Control|Not supported|  
|RDBNAM|Relational Database Name|Supported|  
|RDBRLSOPT|RDB Release Option|Not supported|  
|RDBSRCCOLID|Source Collection Identifier|Not supported|  
|STTDATFMT|Statement Date Format|Not supported|  
|STTDECDEL|Statement Decimal Delimiter|Not supported|  
|STTSTRDEL|Statement String Delimiter|Not supported|  
|STTTIMFMT|Statement Time Format|Not supported|  
|TITLE|Title|Not supported|  
|VRSNAM|Version Name|Supported|  
  
 For more information on Static SQL for DB2 custom package XML schema V85 and V90 formats, see topic titled Package XML Schema.
