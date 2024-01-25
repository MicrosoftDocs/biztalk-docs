---
description: "Learn more about: Schema should have segments in the following order ST .... SE"
title: "Schema should have segments in the following order ST .... SE"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Schema should have segments in the following order ST .... SE
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                    SchemaCode116ETransactionSetSchemaStSeOutOfOrder                    |
|  Message Text   |             Schema should have segments in the following order ST .... SE              |
  
## Explanation  
 This Error/Warning/Information event indicates that a custom document schema is invalid because the headers and trailers were not in the correct order. BizTalk Server performs this validation when the schema is deployed.  
  
## User Action  
 To resolve this error, change the customized document schema so that the headers and trailers are in the correct order, and then redeploy the schema.
