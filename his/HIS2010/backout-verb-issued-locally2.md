---
title: "BACKOUT Verb Issued Locally2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ba03e65-c8fc-4470-87af-8275db923323
caps.latest.revision: 3
---
# BACKOUT Verb Issued Locally
![](../core/media/appc2db.gif "appc2db")  
BACKOUT verb issued locally.  
  
1.  The local transaction program issues a [RECEIVE_AND_WAIT](../HIS2010/receive-and-wait1.md) or [MC_RECEIVE_AND_WAIT](../HIS2010/mc-receive-and-wait1.md) verb (depending on whether a basic or mapped conversation is being used) to receive data from the remote transaction program. The vendor API passes the verb transparently to Host Integration Server.  
  
2.  The **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** verb completes with the **what_rcvd** field of the VCB set to AP_PS_HEADER. The data buffer contains a PREPARE PS header.  
  
3.  Another **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** verb is issued by the vendor API to receive the send indication from the remote TP.  
  
4.  The vendor API returns the transaction program's **RECEIVE_AND_WAIT** or **MC_RECEIVE_AND_WAIT** verb with the **what_rcvd** field of the VCB set to **TAKE_SYNCPT**.  
  
5.  The transaction program issues a **BACKOUT** verb to back out the transaction.  
  
6.  The vendor API generates a [SEND_ERROR](../HIS2010/send-error1.md) or [MC_SEND_ERROR](../HIS2010/mc-send-error1.md) verb of type BACKOUT_RESYNC to send the Backout sense code 0x08240001.  
  
7.  The vendor API then issues a [CONFIRM](../HIS2010/confirm1.md) or [MC_CONFIRM](../HIS2010/mc-confirm1.md) verb to flush the **SEND_ERROR** or **MC_SEND_ERROR** verb and request a response from the remote transaction program.  
  
8.  The [CONFIRM](../HIS2010/confirm1.md) or [MC_CONFIRM](../HIS2010/mc-confirm1.md) verb completes when the remote transaction program issues a [CONFIRMED](../HIS2010/confirmed2.md) or [MC_CONFIRMED](../HIS2010/mc-confirmed2.md) verb. The vendor API then returns the **BACKOUT** verb to the local transaction program.