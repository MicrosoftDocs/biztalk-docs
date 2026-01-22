---
description: "Learn more about: Resend Status Details Page UI"
title: Resend Status Details Page UI
TOCTitle: Resend Status Details Page UI
ms:assetid: 5265b0b5-a5db-4a3d-9574-286fe39a0b01
ms:mtpsurl: https://msdn.microsoft.com/library/Dd792686(v=BTS.80)
ms:contentKeyID: 51528050
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
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
> <P>This value overrides the <STRONG>Retry count</STRONG> specified in the <STRONG>Transport Advanced Options</STRONG> page of the send port.</P>



**Interval between retries**  
Displays the time between resend attempts by the HTTP adapter.


> [!NOTE]
> <P>This value overrides the <STRONG>Retry interval</STRONG> specified in the <STRONG>Transport Advanced Options</STRONG> page of the send port.</P>



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

