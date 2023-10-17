---
description: "Learn more about: A failure occurred in processing X12 message on send port: No Party with name"
title: "A failure occurred in processing X12 message on send port: No Party with name"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# A failure occurred in processing X12 message on send port: No Party with name
## Details  
  
|     Parameter         |                   Value                                                                 |
|-----------------|-----------------------------------------------------------------------------------------------|
|  Product Name   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]       |
| Product Version |                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                   |
|    Event ID     |                                               -                                               |
|  Event Source   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI     |
|    Component    |                                          EDI Engine                                           |
|  Symbolic Name  |                                               -                                               |
|  Message Text   | A failure occurred in processing X12 message on send port {0}. No Party exists with name {1}. |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was unable to resolve the party for the X12 interchange because BizTalk Server was unable to match the send port that subscribed to the interchange with the send port associated with a party. This occurs if neither the DestinationPartyName property, nor the sender qualifier, sender identifier, receiver qualifier, and receiver identifier properties, are promoted, so are unavailable for send-side party resolution.  
  
## User Action  
 To resolve this error, ensure the send port that subscribed to the interchange matches the send port associated with a party.
