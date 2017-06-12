---
title: "Update batch. application x-www-form-urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 94bd7f1b-a4f7-4b36-9d94-58c4d32fc345
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update batch.: application/x-www-form-urlencoded
## Update batch.


  Response Content Type: **application/x-www-form-urlencoded**

Parameters
---


Parameter|Value|Description|Parameter Type|Data Type 
---------|---------|---------|---------|---------
batchDescription|(required)|The batch description.|body  |         |
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
  "StartDate": "2017-04-24T00:09:02.572Z",
  "EndDate": "2017-04-24T00:09:02.572Z",
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
    "FirstRelease": "2017-04-24T00:09:02.573Z",
    "SendEmptyBatchSignal": true
  }
}
```

Response Messages
---


HTTP Status Code|Reason|Response Model|Headers  
---------|---------|---------|---------
204     |No Content |         |         |

