---
title: "pCSInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23afe04d-d984-493c-81db-3078c525f852
caps.latest.revision: 4
---
# pCSInfo
## Syntax  
  
```  
  
struct cs_info {  
    unsigned short  length;  
    unsigned char   major_ver;  
    unsigned char   minor_ver;  
    unsigned char   config_share[80];  
    unsigned short  nos;  
};  
```  
  
## Members  
 *length*  
 Length of the data structure supplied by the application.  
  
 *major_ver*  
 Major version number:  
  
 1 for Communications Server 1.1  
  
 2 for SNA Server 2.0 or 2.1  
  
 3 for SNA Server 3.0  
  
 4 for SNA Server 4.0  
  
 *minor_ver*  
 Minor version number (decimal):  
  
 10 for Communications Server 1.1  
  
 00 for SNA Server 2.0  
  
 20 for SNA Server 2.1  
  
 00 for SNA Server 3.0  
  
 00 for SNA Server 4.0  
  
 *config_share[80]*  
 The name of the share point of the current configuration file (\\\server\share\\, for example). This path name must be a null-terminated string.  
  
 *nos*  
 Transport protocol in use:  
  
 bit 0: LAN Manager/LAN Server (named pipes)  
  
 bit 4: TCP/IP