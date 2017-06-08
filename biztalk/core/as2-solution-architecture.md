---
title: "AS2 Solution Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41e493ba-919b-4520-9c12-92d6757984ef
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Solution Architecture
AS2 processing is performed separately from EDI processing. AS2 messages are received, processed, and an acknowledgment sent apart from the processing of the EDI payload. As a result, AS2 processing is designed and configured apart from EDI processing. In addition, you can use AS2 to transport either EDI messages or non-EDI messages.  
  
 This section describes the architecture of AS2 solutions on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], including end-to-end, receive-side, and send-side processing.  
  
## In This Section  
  
-   [AS2 Messaging](../core/as2-messaging.md)  
  
-   [The Role of Agreements in AS2 Processing](../core/the-role-of-agreements-in-as2-processing.md)  
  
-   [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md)  
  
-   [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md)