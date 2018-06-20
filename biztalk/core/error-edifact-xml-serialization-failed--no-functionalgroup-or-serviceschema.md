---
title: "Edifact interchange Xml serialization failed due to invalid structure, no FunctionalGroup or ServiceSchema | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 530faadd-e301-4743-b4b3-b04ba7578f1d
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Edifact interchange Xml serialization failed due to invalid structure, no FunctionalGroup or ServiceSchema
## Details  
  
|                 |                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                              |
| Product Version |                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                          |
|    Event ID     |                                                                      -                                                                       |
|  Event Source   |                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                            |
|    Component    |                                                                  EDI Engine                                                                  |
|  Symbolic Name  |                                                                      -                                                                       |
|  Message Text   | Edifact interchange Xml serialization failed due to invalid structure. Looking for FunctionalGroup or ServiceSchema for UNZ, but none found. |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process an EDIFACT batched interchange that was preserved because the TransactionSetGroup or FunctionalGroup tags were not included in the interchange XML file.  
  
 When BizTalk processes a batched interchange that is preserved, a group of transaction sets or a group of groups in the interchange's XML file are given an XML tag. A group of groups is given the FunctionalGroup tag. The ServiceSchema flag indicates the control schema used for the preserved-batch interchange. This error condition occurs if you set up a preserved batch using a receive pipeline and a passthrough transmit send pipeline. The tags are set by the receive pipeline and stripped out by the send pipeline.  
  
## User Action  
 To resolve this error, ensure that the XML file generated for the preserved batch has a well-formed XML structure with the FunctionalGroup tag (for multiple groups) and/or the ServiceSchema tag (for the control schema used for the preserved-batch interchange).