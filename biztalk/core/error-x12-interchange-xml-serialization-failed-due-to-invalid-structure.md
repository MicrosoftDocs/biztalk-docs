---
description: "Learn more about: X12 interchange Xml serialization failed due to invalid structure. Looking for TransactionSet or GE, but not found"
title: "X12 interchange Xml serialization failed due to invalid structure. Looking for TransactionSet or GE, but not found"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# X12 interchange Xml serialization failed due to invalid structure. Looking for TransactionSet or GE, but not found
## Details  
  
| Field | Error Details | 
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| Product Version |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                             |
|    Event ID     |                                                         -                                                          |
|  Event Source   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI               |
|    Component    |                                                     EDI Engine                                                     |
|  Symbolic Name  |                                           X12TransactionSetOrGeNotFound                                            |
|  Message Text   | X12 interchange Xml serialization failed due to invalid structure. Looking for TransactionSet or GE, but not found |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not serialize the outgoing interchange because the structure of the interchange was invalid. The reason could be that the required headers or trailers are not present or are invalid. It could occur if a transaction set in a group is not followed by another transaction set or the group trailer. It could also occur if structural integrity checks failed.  
  
## User Action  
 To resolve this error, verify the structure of the interchange, ensuring that the group or transaction set headers and trailers are valid, and then resend the interchange.
