---
description: "Learn more about: Batch message cannot be serialized as there is no party associated with send port"
title: "Batch message cannot be serialized as there is no party associated with send port"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Batch message cannot be serialized as there is no party associated with send port
## Details  
  
|      Field      |                                                       Error Details                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                             |
| Product Version |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                         |
|    Event ID     |                                                                     -                                                                      |
|  Event Source   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                           |
|    Component    |                                                              Batching Engine                                                               |
|  Symbolic Name  |                                             BatchMessageSerializationFailureDueToMissingParty                                              |
|  Message Text   | Batch message can not be serialized as there is no party associated with send port {0}. Make sure that a party is associated with the port |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process a preserved interchange because it could not determine the party that the message should be sent to. It could not determine the party because the DestinationPartyName context property was not set. As a result, the send pipeline could not determine the envelope settings.  
  
## User Action  
 To resolve this error, pass the message through a passthrough send pipeline, and then determine the DestinationPartyName context property for the message. Verify that the party exists. If not, create the party, and then resend the message.
