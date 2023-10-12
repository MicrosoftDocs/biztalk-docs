---
description: "Learn more about: Import-Copy failed as there are active-pending batches"
title: "Import-Copy failed as there are active-pending batches"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Import-Copy failed as there are active-pending batches
## Details  
  
|  Field               |   Error Details                                                                                                             |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  Product Name   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| Product Version |                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                           |
|    Event ID     |                                                       -                                                        |
|  Event Source   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI             |
|    Component    |                                                   EDI Engine                                                   |
|  Symbolic Name  |                                              Err_ActiveBatchFound                                              |
|  Message Text   | Import/Copy failed as there are active/pending batches. Stop active/pending batches and try importing/copying. |
  
## Explanation  
 This Error/Warning/Information event indicates BizTalk Server was unable to Import a binding file or copy the settings as the affected Agreement(s) have one or more active or pending batch.  
  
## User Action  
 To resolve this error, ensure that all the batches in affected agreements are showing as stopped in the Agreement properties.
