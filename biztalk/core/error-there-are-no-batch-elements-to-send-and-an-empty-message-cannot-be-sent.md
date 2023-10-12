---
description: "Learn more about: There are no batch elements to send and an empty message cannot be sent as it is not configured for party"
title: "There are no batch elements to send and an empty message cannot be sent as it is not configured for party"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# There are no batch elements to send and an empty message cannot be sent as it is not configured for party
## Details  
  
| Field | Error Details | 
|-----------------|---------------------------------------------------------------------------------------------------------------|
|  Product Name   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| Product Version |                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    Event ID     |                                                       -                                                       |
|  Event Source   |            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI             |
|    Component    |                                                Batching Engine                                                |
|  Symbolic Name  |                                            EmptyMessageNotAllowed                                             |
|  Message Text   | There are no batch elements to send and an empty message cannot be sent as it is not configured for party {0} |
  
## Explanation  
 This Warning indicates that no batch message was sent in a schedule-based batching process because no batch elements had been received when the batch release was scheduled, and the empty batch signal has not been enabled.  
  
## User Action  
 To prevent this warning from being posted, configure the empty batch signal by doing the following:  
  
1.  Open the BizTalk Server Administration Console.  
  
2.  Move to the Parties node.  
  
3.  Open the EDI Properties dialog box for the party.  
  
4.  Click the Interchange Batch Creation Settings node (for the appropriate encoding).  
  
5.  Click the Scheduler.  
  
6.  Click the Send empty batch signal property.
