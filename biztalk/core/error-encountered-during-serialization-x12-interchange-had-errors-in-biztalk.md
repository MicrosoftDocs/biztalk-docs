---
description: "Learn more about: Error encountered during serialization. The X12 interchange had the following errors"
title: "Error encountered during serialization. The X12 interchange had the following errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Error encountered during serialization. The X12 interchange had the following errors
## Details  
  
|    Field        |                                           Error Details                                                                                     |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| Product Version |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    Event ID     |                                                                      -                                                                      |
|  Event Source   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                            |
|    Component    |                                                                 EDI Engine                                                                  |
|  Symbolic Name  |                                                           X12InterchangeSendError                                                           |
|  Message Text   | Error encountered during serialization. The X12 interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing X12 interchange because of the stated errors.  
  
## User Action  
 To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.
