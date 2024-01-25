---
description: "Learn more about: The property name is not a valid string"
title: "The property name is not a valid string"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The property name is not a valid string
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                    Batching Engine                                     |
|  Symbolic Name  |                                  InvalidPropertyName                                   |
|  Message Text   |                        The property name is not a valid string                         |
  
## Explanation  
 This Error/Warning/Information event indicates that the name entered for a property in the Batch Filter dialog box was invalid, because the property name was not a string, as required.  
  
## User Action  
 To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box. Make sure that all property names are strings.
