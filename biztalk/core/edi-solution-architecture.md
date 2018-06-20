---
title: "EDI Solution Architecture | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55709a89-7706-4c64-ada3-16951951c943
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Solution Architecture
Electronic Data Interchange (EDI) is one of the most prevalent means by which business entities exchange data electronically. EDI usage entails message syntax and standards (including ANSI X12 and UN/EDIFACT), messaging protocol, and transports. The following are characteristics of EDI messaging:  
  
- EDI messaging protocols ensure that data always arrives as expected, and corrupted or incorrect data is automatically detected and reported.  
  
- EDI mechanisms usually specify data aggregation schemes (batching).  
  
- Users often customize EDI document definitions by implementing subset or specific implementation of an EDI guideline.  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes EDI messages using receive and send pipelines specific to EDI that can parse and serialize EDI messages. This section describes the architecture of EDI solutions on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], including specifics of receive-side and send-side processing, message validation, and status reporting.  
  
## In This Section  
  
-   [EDI Messaging](../core/edi-messaging.md)  
  
-   [The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md)  
  
-   [How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md)  
  
-   [How BizTalk Server Sends EDI Messages](../core/how-biztalk-server-sends-edi-messages.md)  
  
-   [EDI Message Validation](../core/edi-message-validation.md)  
  
-   [Using the XML Tool Extensions](../core/using-the-xml-tool-extensions.md)