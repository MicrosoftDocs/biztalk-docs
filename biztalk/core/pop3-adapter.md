---
title: "POP3 Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "POP3 adapters, about POP3 adapters"
  - "authenticating, POP3 adapters"
  - "POP3 adapters"
  - "POP3 adapters, receive adapters"
  - "POP3 adapters, authenticating"
  - "receive adapters, POP3 adapters"
ms.assetid: 008f7fa7-60c3-4ea3-b90d-821e4029a04c
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# POP3 Adapter
You use the Post Office Protocol 3 (POP3) adapter to retrieve data from a server that houses POP3 mailboxes into a server running Microsoft BizTalk Server by means of the POP3 protocol.  
  
 The POP3 adapter consists of only one adapter, a receive adapter. The receive adapter controls the receive locations that use the POP3 adapter.  
  
 This topic discusses the workflow of the POP3 receive adapter.  
  
 **POP3 Receive Adapter**  
  
 The POP3 receive adapter retrieves e-mail from a specified mailbox on a specified POP3 server. By default, the POP3 receive adapter applies MIME processing to the e-mail messages that it downloads and submits these messages to BizTalk Server as multipart BizTalk messages. The POP3 receive adapter can receive and process e-mail in the following formats:  
  
- Plain text  
  
- MIME encoded  
  
- MIME encrypted  
  
- MIME encoded and signed  
  
- MIME encrypted and signed  
  
  **Batching Support for the POP3 Receive Adapter**  
  
  The POP3 receive adapter does not support batching.  
  
  **Authentication with POP3 Server**  
  
  The following authentication methods are supported for use with the POP3 adapter:  
  
- **Basic.** The POP3 server uses user provided credentials for authentication.  These credentials are sent in clear text.  
  
- **Digest (APOP).** The POP3 server uses a digest string for authentication.  
  
- **Secure Password Authentication (SPA).** The POP3 server uses current process credentials for authentication.  
  
## In This Section  
  
-   [What Is the POP3 Adapter?](../core/what-is-the-pop3-adapter.md)  
  
-   [Configuring the POP3 Adapter](../core/configuring-the-pop3-adapter.md)  
  
-   [Walkthrough: Creating a BizTalk Application That Uses the POP3 Adapter](../core/walkthrough-creating-a-biztalk-application-that-uses-the-pop3-adapter.md)  
  
-   [Processing Multi Part Messages with the POP3 Adapter](../core/processing-multi-part-messages-with-the-pop3-adapter.md)