---
title: "Additional Sync Point Return Codes2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 814ac94d-9bc0-450c-81d1-9a6c37df35b7
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Additional Sync Point Return Codes
When a remote transaction program (TP) issues a **BACKOUT** verb, the back out is reported to the local TP as a new primary return code value, AP_BACKED_OUT, on the next (current) verb issued. The local TP is provided access to the sense code information contained in the Backout FMH-7 by setting the **secondary_rc** field as follows:  
  
-   AP_BO_NO_RESYNC for sense code 0x08240000  
  
-   AP_BO_RESYNC for sense code 0x08240001  
  
 This new return code will only be supplied on conversations with **synclevel** AP_SYNCPT, and therefore will not be presented to existing applications.  
  
 The verbs on which this new return code can be returned are:  
  
 [CONFIRM](../Topic/CONFIRM1.md)  
  
 [MC_CONFIRM](../Topic/MC_CONFIRM1.md)  
  
 [MC_PREPARE_TO_RECEIVE](../Topic/MC_PREPARE_TO_RECEIVE2.md)  
  
 [MC_RECEIVE_AND_POST](../Topic/MC_RECEIVE_AND_POST1.md)  
  
 [MC_RECEIVE_AND_WAIT](../Topic/MC_RECEIVE_AND_WAIT1.md)  
  
 [MC_RECEIVE_IMMEDIATE](../Topic/MC_RECEIVE_IMMEDIATE1.md)  
  
 [MC_SEND_DATA](../Topic/MC_SEND_DATA2.md)  
  
 [MC_SEND_ERROR](../Topic/MC_SEND_ERROR1.md)  
  
 [PREPARE_TO_RECEIVE](../Topic/PREPARE_TO_RECEIVE1.md)  
  
 [RECEIVE_AND_POST](../Topic/RECEIVE_AND_POST2.md)  
  
 [RECEIVE_AND_WAIT](../Topic/RECEIVE_AND_WAIT1.md)  
  
 [RECEIVE_IMMEDIATE](../Topic/RECEIVE_IMMEDIATE2.md)  
  
 [SEND_DATA](../Topic/SEND_DATA2.md)  
  
 [SEND_ERROR](../Topic/SEND_ERROR1.md)