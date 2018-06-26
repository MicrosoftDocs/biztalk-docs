---
title: "The first element of the batch exceeded the character count release criteria set | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4b06f8f-247d-4e93-8c4e-5e86e4ad70c9
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The first element of the batch exceeded the character count release criteria set
## Details  
  
|                 |                                                                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                         |
| Product Version |                                                                                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                                     |
|    Event ID     |                                                                                                                                 -                                                                                                                                  |
|  Event Source   |                                                                                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                                       |
|    Component    |                                                                                                                          Batching Engine                                                                                                                           |
|  Symbolic Name  |                                                                                                                   FirstElementExceededCharCount                                                                                                                    |
|  Message Text   | The first element of the batch exceeded the character count release criteria set. Please change the character count release criteria to be able to process this message. The message will need to be resent to the batching system after the settings are modified |
  
## Explanation  
 This Error/Warning/Information event indicates that the batching orchestration could not generate the batched interchange because the number of characters in the first batch element picked up by the batching orchestration exceeded the number of characters specified by the "Maximum number of characters in an interchange" property of the batch release criteria. Note that the number of characters compared to the maximum does not include the number of characters in the envelope.  
  
## User Action  
 To resolve this error, do one of the following:  
  
1.  Increase the "Maximum number of characters in an interchange" property in the Interchange Batch Creation Settings Page of the EDI Properties dialog box for the party as interchange receiver. To do so, you must stop the orchestration instance, increase the maximum number of characters in the property, and then restart the orchestration instance. Have the sender resend the message.  
  
2.  Have the sender send transaction sets that have fewer characters than the maximum number of characters.