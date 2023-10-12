---
description: "Learn more about: The batch element exceeded the maximum configured character count"
title: "The batch element exceeded the maximum configured character count"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The batch element exceeded the maximum configured character count
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                    Batching Engine                                     |
|  Symbolic Name  |                             MessageExceededCharacterCount                              |
|  Message Text   |           The batch element exceeded the maximum configured character count            |
  
## Explanation  
 This Error/Warning/Information event indicates that the batching orchestration could not generate the batched interchange because the number of characters in a batch element picked up by the batching orchestration exceeds the number of characters specified by the "Maximum number of characters in an interchange" property of the batch release criteria. The batch element that generates this error message will not be the first batch element picked up for a batch, but a batch element after the first element has already been batched. Note that the number of characters compared to the maximum does not include the number of characters in the envelope.  
  
## User Action  
 To resolve this error, do one of the following:  
  
1.  Increase the "Maximum number of characters in an interchange" property in the Interchange Batch Creation Settings Page of the EDI Properties dialog box for the party as interchange receiver. To do so, you must stop the orchestration instance, increase the maximum number of characters in the property, and then restart the orchestration instance.  
  
2.  Have the sender send transaction sets that have fewer characters than the maximum number of characters.
