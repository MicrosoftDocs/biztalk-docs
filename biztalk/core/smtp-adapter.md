---
title: "SMTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SMTP adapters, about SMTP adapters"
  - "SMTP adapters, authenticating"
  - "send adapters, SMTP adapters"
  - "authenticating, SMTP adapters"
  - "SMTP adapters"
  - "SMTP adapters, send adapters"
ms.assetid: b712f76d-3ce4-4780-9627-951e5951bd8a
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SMTP Adapter
You use the Simple Mail Transfer Protocol (SMTP) adapter to exchange information between a server running Microsoft BizTalk Server and other applications by means of the SMTP protocol. BizTalk Server can send messages to other applications by creating an e-mail message and delivering it to a specified e-mail address. Internally, the SMTP send adapter creates an SMTP-based e-mail message and sends it to a target e-mail address. The target e-mail address is a property of the SMTP adapter. BizTalk Explorer exposes this property when you configure the SMTP send port.  
  
 The SMTP adapter supports wildcard characters in the **TO**, **FROM**, **CC** and **SUBJECT** properties, and resolves them to their actual values. If wildcard characters in the **TO**, **FROM**, and **CC** properties cannot be resolved, the SMTP transport logs an error and puts the message into the suspended queue or redirects the message to the backup transport. If the wildcard characters cannot be resolved in the **SUBJECT** property, the message is sent with the **SUBJECT** property specified exactly as in the property (for example, "Message %MessageID%").  
  
 By default, the message text of SMTP messages is plain text. To use HTML in message bodies, you can configure the adapter to use the contents of an HTML file for the message text.  
  
 For more information about SMTP security issues, see [SMTP Adapter Security Recommendations](../core/smtp-adapter-security-recommendations.md).  
  
 The SMTP adapter consists of only one adapter, a send adapter. The send adapter controls the send ports that use the SMTP adapter.  
  
 This topic discusses the flow of a message through the SMTP send adapter.  
  
 **SMTP Send Adapter**  
  
 The SMTP send adapter gets messages from the server and posts them to an SMTP server that sends them to e-mail recipients. The SMTP send adapter gets the message content from the body part of the BizTalk Message object, from a specified file, or from a text entered into a dialog box that is available when configuring the adapter.  
  
 After the SMTP send adapter successfully posts a message onto the SMTP server, the SMTP send adapter deletes the message from the MessageBox database.  
  
 The SMTP send adapter can request delivery notification and read receipts for messages sent over the SMTP send adapter. The SMTP adapter delivers the notification and read receipt to the address specified on the SMTP **From** header.  
  
 **Authentication with SMTP Server**  
  
 If you require SMTP server authentication, the SMTP send adapter uses one of the following authentication types:  
  
-   **Basic.** The SMTP server uses user-provided credentials for authentication.  
  
-   **Process account (NTLM).** The SMTP server uses current process credentials for authentication.  
  
## In This Section  
  
-   [Configuring the SMTP Adapter](../core/configuring-the-smtp-adapter.md)  
  
-   [Restrictions When Configuring the SMTP Adapter](../core/restrictions-when-configuring-the-smtp-adapter.md)  
  
-   [SMTP Adapter Security Recommendations](../core/smtp-adapter-security-recommendations.md)