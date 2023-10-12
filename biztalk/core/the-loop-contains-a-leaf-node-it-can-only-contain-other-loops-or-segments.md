---
description: "Learn more about: The loop contains a leaf node. It can only contain other Loops or Segments"
title: "The loop contains a leaf node. It can only contain other Loops or Segments"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The loop contains a leaf node. It can only contain other Loops or Segments
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                           SchemaCode125ELoopContainsLeafNode                           |
|  Message Text   |       The loop contains a leaf node. It can only contain other Loops or Segments       |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, because the interchange did not conform to the document schema. In this case, a loop contained a childless leaf node, whereas the schema specified that the loop could only contain other loops or segments.  
  
## User Action  
 To resolve this error, have the sender of the interchange fix the loop so that it does not contain leaf nodes, and then resend the interchange.
