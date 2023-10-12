---
description: "Learn more about: Acknowledgement generation has failed as maximum limit of Edifact transaction set control number has been reached for global settings"
title: "Acknowledgement generation has failed as maximum limit of Edifact transaction set control number has been reached for global settings"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Acknowledgement generation has failed as maximum limit of Edifact transaction set control number has been reached for global settings
## Details  
  
|    Field             |     Error Details                                                                                                                                                                                                                                                      |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                     |
| Product Version |                                                                                                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                                 |
|    Event ID     |                                                                                                                             -                                                                                                                             |
|  Event Source   |                                                                                                                    BizTalk Server EDI                                                                                                                     |
|    Component    |                                                                                                                        EDI Engine                                                                                                                         |
|  Symbolic Name  |                                                                                                                             -                                                                                                                             |
|  Message Text   | Acknowledgement generation has failed as max limit of acceptable Edifact transaction set control number has reached for Guest settings. Reset counter by navigating to Global configuration sender role screen, field UNH 1 in Partner Agreement manager. |
  
## Explanation  
 This Error/Warning/Information event indicates that BizTalk Server could not generate an acknowledgment to the EDIFACT interchange because the control number that it entered in the Transaction set reference number (UNH1) of the acknowledgment is greater than the maximum value allowed for UNH1. In this instance, BizTalk Server used the EDI global properties to create the acknowledgment.  
  
 The maximum value of the transaction set reference number depends upon the number of digits used for the reference number. The maximum number of characters is 14 for the reference number, 13 for the prefix and suffix, and 14 for all three fields combined.  
  
## User Action  
 To resolve this error, reset the reference number field (UNH1.2) of the Transaction set reference number (UNH1) in the UNG and UNH Segment Definition Page to a value that is lower than the maximum limit. Set this property in the EDI Global Properties dialog box in the BizTalk Server Administration Console.
