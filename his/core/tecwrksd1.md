---
title: "tecwrksd1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 824bda63-9fe4-40d1-bbcb-0370f4392efb
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# tecwrksd
Tecwrksd is a logical unit (LU)/session information record, which includes details of a 3270 LU.  
  
## Syntax  
  
```  
  
typedef struct tecwrksd {  
    UCHAR   cwshost[9];  
    USHORT  cwsestyp;  
    USHORT  cwsmodov;   
    USHORT  cwspad;  
} TECWRKSD;  
```  
  
## Members  
 *cwshost[9]*  
 LU/pool name accessed.  
  
 *cwsestyp*  
 Session type (M2, M3, M4, M5, printer).  
  
 *cwsmodov*  
 Whether the user has override permission.  
  
 *cwspad*  
 Two bytes of padding.  
  
## Remarks  
 The following "Members" list explains the meaning of each field in the structures and indicates how the application should use each field. For more information about Host Integration Server 3270 configuration, see [Configuration Information](../core/configuration-information1.md).  
  
## Members  
 *cwshost*  
 The name (up to eight characters) of the LU or LU pool that this session is configured to use. The application specifies this name on the [Open(SSCP) Request](./open-sscp-request2.md).  
  
 *cwsestyp*  
 The LU type (display or printer) of the LU used by this session and (if it is a display LU or a pool of display LUs) the screen model. The possible values are:  
  
- CERTMOD2 (0)        Model 2 display (24 by 80)  
  
- CERTMOD3 (1)        Model 3 display (32 by 80)  
  
- CERTMOD4 (2)        Model 4 display (43 by 80)  
  
- CERTMOD5 (3)        Model 5 display (27 by 132)  
  
- CERTPRNT (4)         Host printer  
  
  The application should use this value to distinguish between display and printer sessions and to set the appropriate screen model for display sessions.  
  
  *cwsmodov*  
  **TRUE** if the user has permission to override the screen model for display sessions—that is, to change the session to use a different screen model from the one configured. If this value is **FALSE**, the user should not be permitted to change the screen model. This field is not used for printer sessions and should not be checked.