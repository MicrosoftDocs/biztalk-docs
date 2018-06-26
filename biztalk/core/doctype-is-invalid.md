---
title: "Doctype is invalid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67233aae-65c0-4689-a4b3-60a48132343a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Doctype is invalid
## Details  
  
|                 |                                                                                                                 |
|-----------------|-----------------------------------------------------------------------------------------------------------------|
|  Product Name   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                |
| Product Version |                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                            |
|    Event ID     |                                                        -                                                        |
|  Event Source   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI              |
|    Component    |                                                   EDI Engine                                                    |
|  Symbolic Name  |                                              DocTypeInvalidFormat                                               |
|  Message Text   | Doctype {0} is invalid. It is not possible to determine one or more of namespace, version or transaction set id |
  
## Explanation  
 This Error/Warning/Information event indicates that the EDI receive pipeline was not able to process the incoming interchange, because the schema was not discovered correctly.  
  
 For X12, the target namespace is determined in the "Enable custom transaction set definitions" grid of the X12 Interchange Processing Properties page of the EDI Properties dialog box. The GS02 and ST01 values in the message must match those in a row of the grid, to correctly identify the target namespace. The name of the schema to be used for the transaction set is created by adding the version (the first five characters of GS08) and the doctype (ST01) in the incoming transaction set to the target namespace identified.  
  
 For EDIFACT, the target namespace is determined in the "Enable custom transaction set definitions" grid of the EDIFACT Interchange Processing Properties page of the EDI Properties dialog box. The UNH2.1, UNH2.2, UNH2.3, UNH2.5, UNG2.1, and UNG2.2 values in the message must match those in a row of the grid, to correctly identify the target namespace. The name of the schema to be used for the transaction set is created by adding the message version number in UNH2.2, the message release number in UNH2.3, and the message type in UNH2.1 in the incoming transaction set to the target namespace identified.  
  
## User Action  
 To resolve this error, do as follows:  
  
1.  Ensure that the namespace for the schema for the transaction set is correctly identified by a row in the "Enable custom transaction set definitions" grid of the Interchange Processing Properties page of the EDI Properties dialog box. If not, change the values in the grid.  
  
2.  If the namespace has been correctly identified, determine whether the values that are used to identify the schema are correct. For X12, they are the version (the first five characters of GS08) and the doctype (ST01) in the incoming transaction set. For EDIFACT, they are message version number in UNH2.2, the message release number in UNH2.3, and the message type in UNH2.1 in the incoming transaction set. If the values are incorrectly, have the sender of the transaction set change the values of those fields, and then resend the message.