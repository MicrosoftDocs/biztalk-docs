---
description: "Learn more about: The integer property value is not a valid integer"
title: "The integer property value is not a valid integer"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The integer property value is not a valid integer
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                    Batching Engine                                     |
|  Symbolic Name  |                              InvalidIntegerPropertyValue                               |
|  Message Text   |                   The integer property value is not a valid integer                    |
  
## Explanation  
 This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required an integer value, but the value entered was not an integer.  
  
## User Action  
 To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box. Make sure that the value entered for a property that must be an integer is in fact an integer.
