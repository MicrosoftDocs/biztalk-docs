---
title: "Get batch activation status application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ada2d6f1-3b09-49c2-a64b-990feebb7c9e
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get batch activation status: application/json
## Get batch activation status

  Response Content Type: **application/json**

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
 

