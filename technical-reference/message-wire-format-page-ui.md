---
title: Message Wire Format Page UI
TOCTitle: Message Wire Format Page UI
ms:assetid: 2aead951-d001-4235-9b73-3c19bd5e6f78
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246016(v=BTS.80)
ms:contentKeyID: 51527020
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.edir2.status.message.wire
---

# Message Wire Format Page UI

 

For AS2 messages and their correlated MDNs, the message wire format is stored as a blob stream in the BAM reporting data store. You can display the message wire format (in either text or binary format) by right-clicking an entry in the result of a query in the AS2 Message and Correlated MDN Status Page, and then clicking **View Message Wire Format**.

## General Tab

**Message Type**  
This property specifies the type of the BizTalk message.

For wire format messages, this field will be empty.

**Message ID**  
Displays the unique ID of the message.

For wire format messages this field will contain zeros.

**Part Count**  
Displays the number of parts within the message.

**Body Part Name**  
Displays the name of the body part.

## Context Tab

Use this tab to view system-specific and component-specific properties, such as adapter and pipeline component properties, for the selected message. The properties that appear depend primarily on which component processed the message.

## Message Parts Tab

**Name**  
Displays the name of the message part.

**Character set**  
Displays the encoding of the message.

For wire format messages this field will be empty.

**Content type**  
Displays the format used for the content; most common content types are text/xml, text/plain and text/html.

**Size**  
Displays the message size in bytes.

**Part ID**  
Displays the unique identifier for the message part.

## Body tab.

**Text Tab**  
Click the **Text** tab to view the message in ASCII characters, if the message is decodable.

**Binary Tab**  
Click the **Binary** tab to view the message in binary form.

