---
title: "BACKOUT Verb Issued Locally1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c0cb890-3466-4233-8540-8b3b9eb030f3
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# BACKOUT Verb Issued Locally
![](../core/media/appc2db.gif)  

## What happens
  
1.  The local transaction program issues a [RECEIVE_AND_WAIT](../Topic/RECEIVE_AND_WAIT1.md) or [MC_RECEIVE_AND_WAIT](../Topic/MC_RECEIVE_AND_WAIT1.md) verb (depending on whether a basic or mapped conversation is being used) to receive data from the remote transaction program. The vendor API passes the verb transparently to Host Integration Server.  
  
2.  The **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** verb completes with the **what_rcvd** field of the VCB set to AP_PS_HEADER. The data buffer contains a PREPARE PS header.  
  
3.  Another **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** verb is issued by the vendor API to receive the send indication from the remote TP.  
  
4.  The vendor API returns the transaction program's **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** verb with the **what_rcvd** field of the VCB set to **TAKE_SYNCPT**.  
  
5.  The transaction program issues a **BACKOUT** verb to back out the transaction.  
  
6.  The vendor API generates a [SEND_ERROR](../Topic/SEND_ERROR1.md) or [MC_SEND_ERROR](../Topic/MC_SEND_ERROR1.md) verb of type BACKOUT_RESYNC to send the Backout sense code 0x08240001.  
  
7.  The vendor API then issues a [CONFIRM](../Topic/CONFIRM1.md) or [MC_CONFIRM](../Topic/MC_CONFIRM1.md) verb to flush the **SEND_ERROR** or **MC_SEND_ERROR** verb and request a response from the remote transaction program.  
  
8.  The [CONFIRM](../Topic/CONFIRM1.md) or [MC_CONFIRM](../Topic/MC_CONFIRM1.md) verb completes when the remote transaction program issues a [CONFIRMED](../Topic/CONFIRMED2.md) or [MC_CONFIRMED](../Topic/MC_CONFIRMED2.md) verb. The vendor API then returns the **BACKOUT** verb to the local transaction program.