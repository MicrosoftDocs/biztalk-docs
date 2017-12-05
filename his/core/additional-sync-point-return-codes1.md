---
title: "Additional Sync Point Return Codes1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 837dd2e9-f409-4fbd-82ae-6c6a2b8b58ee
caps.latest.revision: 3
---
# Additional Sync Point Return Codes
When a remote transaction program (TP) issues a **BACKOUT** verb, the back out is reported to the local TP as a new primary return code value, AP_BACKED_OUT, on the next (current) verb issued. The local TP is provided access to the sense code information contained in the Backout FMH-7 by setting the **secondary_rc** field as follows:  
  
-   AP_BO_NO_RESYNC for sense code 0x08240000  
  
-   AP_BO_RESYNC for sense code 0x08240001  
  
 This new return code will only be supplied on conversations with **synclevel** AP_SYNCPT, and therefore will not be presented to existing applications.  
  
 The verbs on which this new return code can be returned are:  
  
 [CONFIRM](../core/confirm1.md)  
  
 [MC_CONFIRM](../core/mc-confirm1.md)  
  
 [MC_PREPARE_TO_RECEIVE](../core/mc-prepare-to-receive2.md)  
  
 [MC_RECEIVE_AND_POST](../core/mc-receive-and-post1.md)  
  
 [MC_RECEIVE_AND_WAIT](../core/mc-receive-and-wait1.md)  
  
 [MC_RECEIVE_IMMEDIATE](../core/mc-receive-immediate1.md)  
  
 [MC_SEND_DATA](../core/mc-send-data2.md)  
  
 [MC_SEND_ERROR](../core/mc-send-error1.md)  
  
 [PREPARE_TO_RECEIVE](../core/prepare-to-receive1.md)  
  
 [RECEIVE_AND_POST](../core/receive-and-post2.md)  
  
 [RECEIVE_AND_WAIT](../core/receive-and-wait1.md)  
  
 [RECEIVE_IMMEDIATE](../core/receive-immediate2.md)  
  
 [SEND_DATA](../core/send-data2.md)  
  
 [SEND_ERROR](../core/send-error1.md)