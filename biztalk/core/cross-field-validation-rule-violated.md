---
description: "Learn more about: Cross field validation rule violated"
title: "Cross field validation rule violated"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Cross field validation rule violated
## Details  
  
|      Field      |                            Error Details                                               |
|-----------------|----------------------------------------------------------------------------------------|
|  Product Name   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| Product Version |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    Event ID     |                                           -                                            |
|  Event Source   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    Component    |                                       EDI Engine                                       |
|  Symbolic Name  |                                           -                                            |
|  Message Text   |                          Cross field validation rule violated                          |
  
## Explanation  
 This Error/Warning/Information event indicates that the X12 interchange failed cross-field validation in the receive pipeline or the send pipeline. This indicates that the X12ConditionDesignator_Check flag is set to "Yes", and that at least one element in the interchange failed a rule identified by the prefix "X12ConditionDesignatorX".  
  
## User Action  
 To resolve this error, do one of the following:  
  
-   Identify which data element failed a cross-field validation rule. Contact the sender of the interchange and indicate that the rule must be followed when creating the interchange.  
  
-   Open the schema for the interchange, and set the X12ConditionDesignator_Check flag for the data element that failed validation to "No".
