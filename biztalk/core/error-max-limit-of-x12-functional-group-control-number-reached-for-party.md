---
description: "Learn more about: Max limit of acceptable X12 functional group control number has reached for party"
title: "Max limit of acceptable X12 functional group control number has reached for party"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Max limit of acceptable X12 functional group control number has reached for party
## Details  
  
| Field | Error Details |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| Product Version |                                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    Event ID     |                                                                                              -                                                                                               |
|  Event Source   |                                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                    |
|    Component    |                                                                                          EDI Engine                                                                                          |
|  Symbolic Name  |                                                                                    PartyX12GsNumberError                                                                                     |
|  Message Text   | Max limit of acceptable X12 functional group control number has reached for party {0}. Reset counter by navigating to Party in receiver role screen, field GS 6 in Partner Agreement manager |
  
## Explanation  
 This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the group control number in the GS06 field specified in the party settings was greater than the maximum allowable value. The maximum number of characters for the group control number is 9.  
  
## User Action  
 To resolve this error, reset the group control number, as follows:  
  
1.  In the EDI Properties dialog box for the party resolved for the interchange, open the GS and ST Segment Definition page for the party as interchange receiver.  
  
2.  Click the Edit field associated with the GS06 field.  
  
3.  Set the group control number to a new value such that the field has nine or fewer digits.
