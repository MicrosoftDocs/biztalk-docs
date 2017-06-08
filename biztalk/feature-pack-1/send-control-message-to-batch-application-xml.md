---
title: "Send control message to batch. application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: a81e9f95-167a-46f5-bba4-ca9a25474c19
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Send control message to batch.: application/xml
## Send control message to batch.

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

string

Parameters
---


Parameter|Value|Description|Parameter Type|Data Type 
---------|---------|---------|---------|---------
senderParty|(required)|The sender of the agreement.|path|string| 
receiverParty|(required)|The receiver of the agreement.|path|string| 
agreementName|(required)|The agreement name.|path|string| 
batchName|(required)|The batch name.|path|string| 
controlAction|Activate, Resume, Override, Terminate|The control command to send to the batch.|path|string| 

