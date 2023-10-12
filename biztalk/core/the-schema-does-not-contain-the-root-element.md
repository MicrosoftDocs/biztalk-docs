---
description: "Learn more about: The schema does not contain the root element"
title: "The schema does not contain the root element"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The schema does not contain the root element
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                             SchemaCode102ENullRootElement                              |
|  Message Text   |                    The schema does not contain the root element {0}                    |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming message or the send pipeline could not process the outgoing message because the schema used to validate the message did not contain the root element.  
  
## User Action  
 To resolve this error, undeploy the document schema, add the root element to the schema, and then redeploy the schema.
