---
title: "SNAGetSystemInfo1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7a11f53-e754-471e-98ea-f33bf47cc613
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SNAGetSystemInfo
SNALink calls the **SNAGetSystemInfo** function to obtain information about the SNA server and the network operating system.  
  
## Syntax  
  
```  
  
INTEGER SNAGetSystemInfo(   
struct cs_info *pCSInfo  
);  
```  
  
#### Parameters  
 *pCSInfo*  
 Pointer to a buffer supplied by the application that contains a data structure in which system information is returned. The application must set the **length** field in this data structure. (For details, see Remarks.) The other fields should be set to nulls or blanks.  
  
## Return Value  
 NO_ERROR  
 OK.  
  
 ERNOCFGSVR  
 No configuration file server available.  
  
 ERMOREDATA  
 Supplied buffer was too small.  
  
## Remarks  
 The application must set the **length** parameter to the length of the **cs_info** structure (86 bytes in the current version). Any other value is rejected. This parameter is used to ensure compatibility with future versions. An application supplying this length will always obtain the information shown, but in future versions it may be possible to specify larger values and obtain further information.  
  
 On successful return, the **cs_info** data structure contains the version number of the SNA server, the path to the current configuration file, and the network operating system over which the SNA server is running.  
  
 If there is no configuration file server available, only the version number fields are valid. The other fields should not be checked.