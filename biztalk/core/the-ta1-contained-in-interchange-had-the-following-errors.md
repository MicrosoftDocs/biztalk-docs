---
description: "Learn more about: The TA1 contained in interchange had the following errors"
title: "The TA1 contained in interchange had the following errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The TA1 contained in interchange had the following errors
## Details  
  
| Field | Error Details |
|-----------------|------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                |
| Product Version |                            [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                            |
|    Event ID     |                                                        -                                                         |
|  Event Source   |              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI              |
|    Component    |                                                    EDI Engine                                                    |
|  Symbolic Name  |                                                   X12TA1Error                                                    |
|  Message Text   | The {0} TA1 contained in interchange with id '{1}', sender id '{2}', receiver id '{3}' had the following errors: |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming TA1 acknowledgment because of the indicated error condition. This may indicate that the acknowledgment does not conform to the TA1Schema.  
  
## User Action  
 To resolve this error, have the sender of the acknowledgment resolve the issue with the acknowledgment, ensuring that the acknowledgment conforms to the TA1Schema, and then resend the acknowledgment.
