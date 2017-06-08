---
title: "Send control message to batch. text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ad70588f-a4a5-4494-80b1-fcf8b7c6b6d3
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Send control message to batch.: text/xml
## Send control message to batch.

  Response Content Type: **text/xml**

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

