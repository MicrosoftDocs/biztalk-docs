---
description: "Learn more about: SNAGetConfigValue"
title: "SNAGetConfigValue2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 900f149c-fc6a-4fdf-aeb6-04dec4602eea
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# SNAGetConfigValue
SNALink calls the **SNAGetConfigValue** function to obtain the value of a specific configuration parameter.  
  
## Syntax  
  
```  
  
USHORT SNAGetConfigValue(  
UCHAR *entryName,  
VOID *pBuffer,  
ULONGbufferLen,  
UCHARparmType,  
ULONG *pRetLength  
);  
```  
  
#### Parameters  
 *entryName*  
 The name of the configuration parameter required.  
  
 *pBuffer*  
 A pointer to a buffer (if the parameter is a string), or a pointer to a LONGINT (if the parameter is an integer).  
  
 *bufferLen*  
 The length of the buffer. Only required if the parameter is TYPESTRING.  
  
 *parmType*  
 TYPESTRING if the parameter is a string.  
  
 TYPELONG if the parameter is an integer.  
  
 *pRetLength*  
 Number of bytes returned if the parameter is TYPESTRING, or number of bytes available if the buffer was too short.  
  
## Return Value  
 NO_ERROR  
 OK.  
  
 ERBADCFG  
 Error reading configuration file.  
  
 ERNOTFND  
 Entry not found in configuration record.  
  
 ERTOOLONG  
 Data available exceeded the size of the buffer.  
  
 ERBADTYPE  
 A bad type was specified for the *parmType* parameter.  
  
## Remarks  
 It is strongly recommended that SNALink read all required configuration parameters at initialization time (when [SNALinkInitialize](../core/snalinkinitialize2.md) is called by the Base).
