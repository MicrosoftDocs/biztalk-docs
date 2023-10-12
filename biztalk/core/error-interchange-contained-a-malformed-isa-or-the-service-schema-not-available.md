---
description: "Learn more about: The interchange contained a malformed ISA or the Service schema was not available"
title: "The interchange contained a malformed ISA or the Service schema was not available"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The interchange contained a malformed ISA or the Service schema was not available
## Details  
  
| Field | Error Details |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| Product Version |                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                             |
|    Event ID     |                                                         -                                                          |
|  Event Source   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI               |
|    Component    |                                                     EDI Engine                                                     |
|  Symbolic Name  |                                                 MalformedIsaError                                                  |
|  Message Text   | The interchange contained a malformed ISA or the Service schema was not available, it is being rejected completely |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, because the ISA or IEA segments in the interchange did not conform to the X12ServiceSchema, or the X12ServiceSchema (in BaseArtifacts.dll) was not deployed.  
  
## User Action  
 To resolve this error, do one of the following:  
  
-   Have the sender of the interchange change the ISA and IEA segments so that they conform to the X12ServiceSchema.  
  
-   Ensure that BaseArtifacts.dll includes the X12ServiceSchema and is deployed. You can do so by opening the BizTalk Server Administration Console, opening the BizTalk EDI Application node and then the Schemas node, and verifying that X12ServiceSchema is listed.
