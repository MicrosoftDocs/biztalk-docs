---
description: "Learn more about: The interchange had structural error. A likely cause is invalid segment terminator due to missing Carriage Line and-or Line Feed seperators"
title: "The interchange had structural error. A likely cause is invalid segment terminator due to missing Carriage Line and-or Line Feed seperators"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The interchange had structural error. A likely cause is invalid segment terminator due to missing Carriage Line and-or Line Feed seperators
## Details  
  
| Field | Error Details |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                   |
| Product Version |                                                                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                                               |
|    Event ID     |                                                                                                                                           -                                                                                                                                           |
|  Event Source   |                                                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                                                                 |
|    Component    |                                                                                                                                      EDI Engine                                                                                                                                       |
|  Symbolic Name  |                                                                                                                        EfactInterchangeStructuralErrorAfterUnb                                                                                                                        |
|  Message Text   | The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error. A likely cause is invalid segment terminator due to missing Carriage Line and/or Line Feed seperators. The part after the error is being suspended, refer to Suspended Queue for details |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline, send pipeline, or batching orchestration could not process the EDIFACT interchange, because a segment in the interchange did not have the required segment terminator. For an incoming interchange, the separators are identified in the UNA Segment, or if the UNA segment is not present, the EfactDelimiters pipeline property. For an outgoing interchange, the separators are identified in the UNA Segment Definition page of the EDI Properties dialog box.  
  
## User Action  
 To resolve this error, ensure that all segments in the interchange have the required segment terminator, and then have the interchange resent.
