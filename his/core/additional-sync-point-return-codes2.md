---
title: "Sync Point Return Codes | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 814ac94d-9bc0-450c-81d1-9a6c37df35b7
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Additional Sync Point Return Codes
When a remote transaction program (TP) issues a **BACKOUT** verb, the back out is reported to the local TP as a new primary return code value, AP_BACKED_OUT, on the next (current) verb issued. The local TP is provided access to the sense code information contained in the Backout FMH-7 by setting the **secondary_rc** field as follows:  
  
- AP_BO_NO_RESYNC for sense code 0x08240000  
  
- AP_BO_RESYNC for sense code 0x08240001  
  
  This new return code will only be supplied on conversations with **synclevel** AP_SYNCPT, and therefore will not be presented to existing applications.  
  
  The verbs on which this new return code can be returned are:  
  
  [CONFIRM](confirm2.md)  
  
  [MC_CONFIRM](mc-confirm2.md)  
  
  [MC_PREPARE_TO_RECEIVE](mc-prepare-to-receive1.md)  
  
  [MC_RECEIVE_AND_POST](mc-receive-and-post2.md)  
  
  [MC_RECEIVE_AND_WAIT](mc-receive-and-wait2.md)  
  
  [MC_RECEIVE_IMMEDIATE](mc-receive-immediate2.md)  
  
  [MC_SEND_DATA](mc-send-data1.md)  
  
  [MC_SEND_ERROR](mc-send-error2.md)  
  
  [PREPARE_TO_RECEIVE](prepare-to-receive2.md)  
  
  [RECEIVE_AND_POST](receive-and-post1.md)  
  
  [RECEIVE_AND_WAIT](receive-and-wait2.md)  
  
  [RECEIVE_IMMEDIATE](receive-immediate1.md)  
  
  [SEND_DATA](send-data1.md)  
  
  [SEND_ERROR](send-error2.md)