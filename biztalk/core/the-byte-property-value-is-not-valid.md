---
description: "Learn more about: The byte property value is not valid"
title: "The byte property value is not valid"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The byte property value is not valid
## Details  
  
| Field | Error Details|
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                    Batching Engine                                     |
|  Symbolic Name  |                                InvalidBytePropertyValue                                |
|  Message Text   |                          The byte property value is not valid                          |
  
## Explanation  
 This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required a byte value, but the value entered was not a byte.  
  
## User Action  
 To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box. Make sure that the value entered for a property that requires a byte value is in fact a byte.
