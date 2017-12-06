---
title: "BACKOUT Verb Issued Remotely2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b60246d7-4fa9-444b-9ddf-b453c131dfd6
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# BACKOUT Verb Issued Remotely

![](../core/media/appc2dc.gif)  

## What happens  
1.  The transaction program issues a [SEND_DATA](../Topic/SEND_DATA2.md) or [MC_SEND_DATA](../Topic/MC_SEND_DATA2.md) verb depending on whether a basic or mapped conversation is being used.  
  
2.  The **SEND_DATA** or **MC_SEND_DATA** VCB is passed transparently through the vendor API to Host Integration Server. When the verb completes the return code from Host Integration Server is returned to the transaction program.  
  
3.  The transaction program issues a **SYNCPT** verb to the vendor API.  
  
4.  The vendor API creates a PREPARE PS header and transmits it by issuing a **SEND_DATA** or **MC_SEND_DATA** verb. For a mapped conversation, the data_type field of the **MC_SEND_DATA** VCB must be set to AP_PS_HEADER.  
  
5.  On completion of the **SEND_DATA** or **MC_SEND_DATA** verb, the vendor API issues a [RECEIVE_AND_WAIT](../Topic/RECEIVE_AND_WAIT1.md) or [MC_RECEIVE_AND_WAIT](../Topic/MC_RECEIVE_AND_WAIT1.md) verb.  
  
6.  The **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** verb returns with a return code of AP_BACKED_OUT, indicating that the remote transaction program issued a **BACKOUT** verb.  
  
7.  The vendor API issues another **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** verb to receive the Confirm indication.  
  
8.  When the verb completes with the **what_rcvd** field of the VCB set to AP_CONFIRM, the vendor API issues a [CONFIRMED](../Topic/CONFIRMED2.md) or [MC_CONFIRMED](../Topic/MC_CONFIRMED2.md) verb to acknowledge the **BACKOUT** verb.  
  
9. The **SYNCPT** verb is returned to the transaction program with a BACKED_OUT return code when the **CONFIRMED** or **MC_CONFIRMED** verb completes.