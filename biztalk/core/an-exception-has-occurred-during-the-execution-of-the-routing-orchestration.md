---
description: "Learn more about: An exception has occurred during the execution of the routing orchestration"
title: "An exception has occurred during the execution of the routing orchestration"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# An exception has occurred during the execution of the routing orchestration
## Details  
  
|  Field      |                               Error Details                                                            |
|-----------------|------------------------------------------------------------------------------------------------|
|  Product Name   |       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]       |
| Product Version |                   [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                   |
|    Event ID     |                                               -                                                |
|  Event Source   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI     |
|    Component    |                                        Batching Engine                                         |
|  Symbolic Name  |                                 ExceptionOccuredDuringRouting                                  |
|  Message Text   | An exception has occured during the execution of the routing Orchestration. ErrorMessage = {0} |
  
## Explanation  
 This Error/Warning/Information event indicates that the routing orchestration could not process each copy of the XML batch element correctly because of the error condition indicated in ErrorMessage field.  
  
## User Action  
 To resolve this error, determine what the error condition is from the ErrorMessage field, resolve the error, and resubmit the message.
