---
title: "Edifact interchange should have contained TransactionSetGroup or FunctionalGroup Xml tags | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34318133-211f-422d-acdf-b841ece5d2b0
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Edifact interchange should have contained TransactionSetGroup or FunctionalGroup Xml tags
## Details  
  
|                 |                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------|
|  Product Name   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]     |
| Product Version |                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                 |
|    Event ID     |                                             -                                             |
|  Event Source   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI   |
|    Component    |                                        EDI Engine                                         |
|  Symbolic Name  |                                             -                                             |
|  Message Text   | Edifact interchange should have contained TransactionSetGroup or FunctionalGroup Xml tags |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process an EDIFACT batched interchange that was preserved because the TransactionSetGroup or FunctionalGroup tags were not included in the interchange XML file.  
  
 When BizTalk processes a batched interchange that is preserved, a group of transaction sets or a group of groups in the interchange's XML file are given an XML tag. A group of transaction sets is given the TransactionSetGroup tag. A group of groups is given the FunctionalGroup tag. This error condition occurs if you set up a preserved batch using a receive pipeline and a passthrough transmit send pipeline. The tags are set by the receive pipeline and stripped out by the send pipeline.  
  
## User Action  
 To resolve this error, ensure that the XML file generated for the preserved batch has a well-formed XML structure with the TransactionSetGroup tag (for a group with multiple transaction sets) and/or the FunctionalGroup tag (for multiple groups).