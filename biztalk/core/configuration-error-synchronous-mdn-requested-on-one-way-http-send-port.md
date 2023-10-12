---
description: "Learn more about: Configuration error. Synchronous MDN requested on one way HTTP send port"
title: "Configuration error. Synchronous MDN requested on one way HTTP send port"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configuration error. Synchronous MDN requested on one way HTTP send port
## Details  
  
|      Field      |                            Error Details                                               |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |       Configuration error. Synchronous MDN requested on one way HTTP send port.        |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not receive a synchronous MDN after sending an AS2 message because the HTTP send port that sent the AS2 message was a one-way port. A two-way solicit-response send port is required to process a synchronous MDN returned in response to an AS2 message sent by the port. In this case, the MDN must be returned synchronously because in the configuration for the party as an AS2 Message Receiver, the Request MDN property is checked, and the Request asynchronous MDN property is cleared.  
  
## User Action  
 To resolve this error, change the send port that is sending the AS2 message to be a static solicit-response send port, rather than a one-way send port. Set the receive pipeline of the solicit-response send port to be AS2EdiReceive for an EDI interchange or AS2Receive for a non-EDI interchange.
