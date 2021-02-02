---
description: "Learn more about: Non-printable Character Problems"
title: "Non-printable Character Problems1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ddca5d1-1eef-4dc4-98cf-ce1897b3783a
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Non-printable Character Problems
Characters below 0x40 in the 3270 datastream are considered "non-printable" characters. Some of these values are used by 3270 Orders and SCS codes. By default, if Host Print Service encounters a non-printable character that is not an SCS code or 3270 Order, it rejects the frame, or in some cases translates the character to an ASCII space and continues on. To force Host Print Service to process all characters, and translate them to their ASCII equivalents according to the code page being used, a registry entry has been made available. To add this entry, find the following key using REGEDT32:  
  
```  
HKEY_LOCAL_MACHINE  
   SYSTEM  
     CurrentControlSet  
       Services  
         SnaPrint  
           Parameters  
  
```  
  
 Add the following value to this key:  
  
```  
Value Name:  HonorCharsUnder0x40  
Data Type:  REG_SZ  
String:  TRUE  
  
```
