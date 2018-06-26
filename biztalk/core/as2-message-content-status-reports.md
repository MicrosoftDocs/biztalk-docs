---
title: "AS2 Message Content Status Reports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6244aa59-a80d-450b-ab95-9a5e14c0c40e
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Message Content Status Reports

## Overview
These status reports display the context properties, headers and payload of an AS2 message or an MDN. There are three AS2 message content status reports:  
  
- Message Wire Format report  
  
- Message Decoded Format report  
  
- Mdn Message report  
  
  You display one of these reports by right-clicking an AS2 message within the AS2/MDN status report, and then clicking **View Message Wire Format**, **View Message Decoded Format**, or **View Mdn Message**. The MDN command will display the MDN that is correlated to the AS2 message.  
  
  Each of these reports is available only if you have selected the corresponding "Store messages in non-repudiation database" properties in the Party as AS2 Message Sender page or Party as AS2 Message Receiver page of the AS2 Properties dialog box for the related party. The commands store AS2 messages or MDNs in wire format or decoded format in the BizTalkDTADb database.  
  
  This report uses the **Message Details Properties Dialog Box** (see the UI details [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]) to display message data, with information separated into pages:  
  
|Page|Data Displayed|  
|----------|--------------------|  
|**General**|Overview information about the message|  
|**Context**|Context properties associated with this message|  
|**Message Parts**|Individual document payload contained within this message. Each document can be viewed as either text or binary:<br /><br /> -   Text Format view shows the contents of the AS2 message or MDN in human-readable form, as in an EDI text file. This view shows the AS2 headers, EDI trailers, and EDI payload, with each segment on a separate line.<br />-   Binary Format view shows the contents of the AS2 message or MDN in non-delimited text format and a table of the hexadecimal representations for each ASCII character in the AS2 message or MDN.|