---
title: "Resend Status Details Page UI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5265b0b5-a5db-4a3d-9574-286fe39a0b01
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Resend Status Details Page UI
For AS2 messages and their correlated MDNs, if the **Party as AS2 Message Receiver** page of party properties is configured to resend the AS2 message if an MDN is not received, a **Resend Status Details** report will be available for AS2 messages sent to this party. You can display this report by right-clicking an entry in the result of a query in the AS2 Message and Correlated MDN Status Page, and then clicking **View Reliable Message Status**.  
  
## General  
 **Sender party**  
 Contains the name of the party that is sending the AS2 message.  
  
 **Receiver party**  
 Contains the name of the party that the AS2 message is sent to.  
  
 **AS2 From**  
 Displays the value of the AS2 From field of the message.  
  
 **AS2 To**  
 Displays the value of the AS2 To field of the message.  
  
 **Message ID**  
 Displays the unique ID of the message.  
  
 **Resend index**  
 Displays the number of resends that have occurred for the message.  
  
 **Number of Retries**  
 Displays the number of times the HTTP adapter will attempt to resend the message.  
  
> [!NOTE]
>  This value overrides the **Retry count** specified in the **Transport Advanced Options** page of the send port.  
  
 **Interval between retries**  
 Displays the time between resend attempts by the HTTP adapter.  
  
> [!NOTE]
>  This value overrides the **Retry interval** specified in the **Transport Advanced Options** page of the send port.  
  
 **Maximum retry time**  
 The maximum length of time that the HTTP adapter will attempt to resend the message.  
  
 **Number of resends**  
 Displays the number of times the message should be resent  
  
 **Interval between resends**  
 Displays the minimum time to wait for an MDN before resending the message.  
  
 **Maximum resend time**  
 Displays the maximum length of time that resends will be allowed.  
  
## Resend History  
 **Index**  
 The index of the retry attempt.  
  
 **Event**  
 The status of the retry attempt.  
  
 **Time**  
 The time that the retry attempt was made.