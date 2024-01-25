---
description: "Learn more about: EDI Transaction Set-Message Structural Element"
title: "EDI Transaction Set-Message Structural Element"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# EDI Transaction Set-Message Structural Element
The transaction set (in X12 encoding) or message (in EDIFACT encoding) contains segments that make up the message data. The transaction set consists of a header, a collection of data segments, and a trailer. All details that are required to process the transaction are available within the transaction set.  
  
 A transaction set must start with a ST Transaction Set Header (in X12) or a UNH Message Header (in EDIFACT). It must end with a SE Transaction Set Trailer (in X12) or a UNT Message Trailer (in EDIFACT). The trailer provides a count of the data segments that includes the header and trailer segments.  
  
 A transaction set can contain one or more loops, which are required to repeat a collection of related segments.
