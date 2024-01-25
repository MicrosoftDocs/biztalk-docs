---
description: "Learn more about: An exception has occurred during the batch submission in the batching orchestration"
title: "An exception has occurred during the batch submission in the batching orchestration"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# An exception has occurred during the batch submission in the batching orchestration

## Details  
  
| Error category  | Error details                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                  |
| Product Version |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                              |
|    Event ID     |                                                          -                                                          |
|  Event Source   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                |
|    Component    |                                                   Batching Engine                                                   |
|  Symbolic Name  |                                                  ExceptionOccurred                                                  |
|  Message Text   | An exception has occurred during the batch submission in the batching Orchestration. Batch Id= {0}, ErrorMessage {1}|
  
## Explanation  

This Error/Warning/Information event indicates that the batching orchestration could not add a batch element to a batch because of the error condition indicated in the ErrorMessage field.  
  
## User Action  

To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and then resubmit the message.
