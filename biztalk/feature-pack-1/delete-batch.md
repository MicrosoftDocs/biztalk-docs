---
title: "Delete batch. | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 3976b621-e261-438d-9bc6-b7678f6680f9
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# DELETE /Batches/{senderParty}/{receiverParty}/{agreementName}/{batchName}
## Delete batch.


Parameters
---

Parameter|Value |Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
senderParty|(required)|The sender of the agreement.|path|string |
receiverParty|(required)|The receiver of the agreement.|path|string|
agreementName|(required)|The agreement name.|path|string|
|batchName|(required)|The batch name.|path|string|



Response Messages
---

HTTP Status Code|Reason|Response Model|Headers  
---------|---------|---------|---------
204     |No Content  |         |        | 

