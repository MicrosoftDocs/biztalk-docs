---
title: "sepdgetinfo1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e11313c3-aba6-4684-b4be-85aeae718e25
caps.latest.revision: 4
---
# sepdgetinfo
The **sepdgetinfo** function returns a structure containing the version number of Host Integration Server 2010, the path of the current configuration file, and the network operating system over which Host Integration Server is running.  
  
## Syntax  
  
```  
  
USHORT sepdgetinfo(   
struct cs_info *pCSInfo   
);  
```  
  
#### Parameters  
 *pCSInfo*  
 Pointer to a buffer supplied by the application, containing a **cs_info** data structure in which system information is returned. The application must set the **length** member in this data structure (for more information, see Remarks later in this topic); the other members should be set to nulls or blanks.  
  
## The cs_info structure  
 The returned **cs_info** structure and its members are as follows:  
  
```  
struct cs_info {  
    unsigned short length;  
    unsigned char  major_ver;  
    unsigned char  minor_ver;  
    unsigned char  config_share[80];  
    unsigned short nos;  
 } cs_info;  
```  
  
## Members  
 **length**  
 Length of the data structure supplied by the application.  
  
 **major_ver**  
 Major version number:  
  
 1 for Host Integration Server 1.1 (Connection Server 1.1) 2 for Host Integration Server 2.0 (Connection Server 2.0)  
  
 **minor_ver**  
 Minor version number (decimal):  
  
 10 for Connection Server 1.1 (indicates 1.10)00 for Connection Server 2.0 (indicates 2.00)  
  
 **config_share[80]**  
 Path of the running configuration file`:` \\\server\share\ (null terminated).  
  
 **nos**  
 Network operating system in use  
  
 1: LAN Manager  
  
## Return Value  
 NO_ERROR (0)  
 OK.  
  
 NOCSSRVR (1)  
 No configuration file server available.  
  
 BADLNGTH (2)  
 Supplied buffer was too small.  
  
## Remarks  
 The application must set the **length** member to the length of the **cs_info** structure (86 bytes in the current version). Any other value will be rejected. This parameter is used to ensure compatibility with future versions; an application supplying this length will always obtain the information shown here, but in future versions it may be possible to specify larger values and obtain further information.  
  
 On successful return, the data structure **cs_info** contains the version number of Host Integration Server 2010, the path of the current configuration file, and the network operating system over which Host Integration Server is running.  
  
 If there is no configuration file server available, only the version number fields are valid; the other fields should not be checked.