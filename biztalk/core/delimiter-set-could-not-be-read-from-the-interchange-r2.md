---
title: "Delimiter set could not be read from the interchange (R2) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17bdd32e-d43f-4f59-af27-5d3054fd5432
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Delimiter set could not be read from the interchange (R2)
## Details  

|                 |                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                     |
| Product Version |                                [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                 |
|    Event ID     |                                                             -                                                             |
|  Event Source   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                   |
|    Component    |                                                        EDI Engine                                                         |
|  Symbolic Name  |                                                             -                                                             |
|  Message Text   | Delimiter set could not be read from the interchange. The attribute DelimiterSetSerializedData is missing from root node. |

## Explanation  
 This error indicates the interchange does not contain the delimiter set values.  

## User Action  
 To resolve this error, do one of the following:  

- Add delimiter set values to the interchange, as follows:  

  1.  Open up the message.  

  2.  Determine whether there is a UNA segment in the interchange. If there is not a UNA segment, ask the partner to add the UNA segment to the interchange.  

- Enter the delimiter values to the EfactDelimiters pipeline property, as follows:  

  1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location or send port using the pipeline that you want to set properties for. Click **Properties**.  

  2. Click the ellipsis button (…) next to the pipeline that you want to set properties for.  

  3. Enter values for the UNA delimiters as a comma-delimited list (for UNA1, UNA2, UNA3, UNA4, UNA5, and UNA6), changing the defaults as required. The defaults are as follows: 0x3A, 0x2B, 0x2C, 0x3F, 0x20, 0x27.  

  4. Click **OK**.
