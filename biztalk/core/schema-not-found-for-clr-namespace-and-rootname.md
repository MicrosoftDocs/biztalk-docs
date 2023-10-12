---
description: "Learn more about: Schema not found for CLR Namespace and rootName"
title: "Schema not found for CLR Namespace and rootName"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Schema not found for CLR Namespace and rootName
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                               SchemaNotFoundForCLRAndRN                                |
|  Message Text   |              Schema not found for CLR Namespace = {0} and rootName = {1}               |
  
## Explanation  
 This Error/Warning/Information event indicates that the receive pipeline could not find the document schema using the root name associated with the interchange and the namespace associated with the party that was resolved for the interchange.  
  
## User Action  
 To resolve this error, ensure that the root name taken from the interchange and the namespace determined from the properties of the resolved party correspond together to a deployed schema. BizTalk determines the root name from the document type and version in the interchange. BizTalk determines the schema from the Default Target Namespace field (for default schemas) or the "Enable custom transaction set definitions" grid (for custom schemas) in the Interchange Processing Properties.
