---
title: "Message cannot be serialized as the schema could not be located | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37897c04-650d-4695-846d-b8ba61365647
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message cannot be serialized as the schema could not be located
## Details  
  
|                 |                                                                                                                                          |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                            |
| Product Version |                                        [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                        |
|    Event ID     |                                                                    -                                                                     |
|  Event Source   |                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                          |
|    Component    |                                                                EDI Engine                                                                |
|  Symbolic Name  |                                              MessageSerializationFailureDueToMissingSchema                                               |
|  Message Text   | Message can not be serialized as the schema {0} could not be located. Either the schema is not deployed or multiple copies are deployed. |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not serialize the outgoing interchange because the pipeline could not determine the schema that it needed to use to serialize the interchange. The schema was either not deployed or multiple copies of the schema were deployed.  
  
## User Action  
 To resolve this error, do one of the following:  
  
1.  If the schema associated with the interchange has not been deployed, open Visual Studio, add the schema to a BizTalk project, and then build and deploy the project.  
  
2.  If more than one copy of the schema has been deployed, open Visual Studio, and undeploy all but one of the copies of the schema associated with the interchange.