---
title: "Host Column Description File Format | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2bb551d-68a6-4d52-9e0d-9c0c21572ed4
caps.latest.revision: 4
---
# Host Column Description File Format
The Microsoft® OLE DB Provider for AS/400 and VSAM uses a host column description (HCD) file to describe the format of data files on IBM mainframes and dictate how the data in columns or fields in these files is to be converted by the OLE DB provider. Host column description files can also be used for data on AS/400 computers to override the data format description maintained by the AS/400 host.  
  
 The default naming convention for the HCD file is \<*data source>*.hcd, where \<*data source*> is the remote LU alias, and .hcd is the file name extension of the record description file. For example, if the remote LU alias configured on Host Integration Server is named ABC01234, the host column description file would be named ABC01234.hcd as the default. Any name may be used for an HCD file as long as the file name extension is .hcd.  
  
 All the Virtual Storage Access Method (VSAM) files that have local record descriptions are listed in the [Files] section of the record description file. Each file that is listed in the [Files] section has a record description section, and that section name is the same as the file name. For example, a VSAM file named PUBS/AUTHORS has its record description saved in the [PUBS/AUTHORS] section.  
  
 The first key of a record description section is the number of the columns for the file. The syntax is as follows:  
  
```  
numcol=<number of columns>  
```  
  
 Where *\<number of columns>* is the actual number of columns described in the section*.* Each column of a file is described by one key. The naming convention for the key name is as follows:  
  
```  
col<column number>  
```  
  
 For example the ninth columns key is **col9**. Each key has an attribute list that contains eleven concatenated attributes that describe the column. Attributes are separated by semicolons.