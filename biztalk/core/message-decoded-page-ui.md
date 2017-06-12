---
title: "Message Decoded Page UI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edir2.status.message.decoded"
ms.assetid: 79f14504-9a09-42c1-ae6a-0f65e2c19cbd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Decoded Page UI
For AS2 messages and their correlated MDNs, the decoded AS2 message is stored as a blob stream in the BAM reporting data store. You can display the decoded message (in either text or binary format) by right-clicking an entry in the result of a query in the AS2 Message and Correlated MDN Status Page, and then clicking **View Message Decoded Format**.  
  
## General Tab  
 **Message Type**  
 This property specifies the type of the BizTalk message.  
  
 For decoded messages, this field may be empty.  
  
 **Message ID**  
 Displays the unique ID of the message.  
  
 For decoded messages this field may contain zeros.  
  
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
  
 For decoded messages this field may be empty.  
  
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