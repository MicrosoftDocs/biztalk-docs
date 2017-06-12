---
title: "Get a single batch from one party to another text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 21c27ed5-89fb-48b2-98d7-f1d7fb06252b
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get a single batch from one party to another: text/json
## Get a single batch from one party to another


  Response Content Type: **text/json**

Request
---
Response Class (Status 200)

OK

Parameters
---


Parameter|Value|Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
senderParty|(required)|The sender of the agreement.|path|string|
receiverParty|(required)|The receiver of the agreement.|path|string|
agreementName|(required)|The agreement name.|path|string|
batchName|(required)|The batch name.|path|string|



Example Value
---

```
{
  "Id": 0,
  "Name": "string",
  "Description": "string",
  "Protocol": "string",
  "StartDate": "2017-04-24T00:09:02.538Z",
  "EndDate": "2017-04-24T00:09:02.538Z",
  "TerminationCount": 0,
  "Filter": {
    "Groups": [
      {
        "Statements": [
          {
            "Property": "string",
            "Operator": "string",
            "Value": "string"
          }
        ]
      }
    ]
  },
  "MessageCountRelease": {
    "MessageScope": "string",
    "MessageCount": 0
  },
  "ManualRelease": {},
  "InterchangeSizeRelease": {
    "CharacterCount": 0
  },
  "TimeBasedRelease": {
    "WeeklyRecurrence": {
      "WeekDays": "string",
      "RecurrencePeriod": "string"
    },
    "HourlyRecurrence": {
      "Hours": 0,
      "Minutes": 0,
      "RecurrencePeriod": "string"
    },
    "DailyRecurrence": {
      "Days": 0,
      "RecurrencePeriod": "string"
    },
    "FirstRelease": "2017-04-24T00:09:02.538Z",
    "SendEmptyBatchSignal": true
  }
}
```