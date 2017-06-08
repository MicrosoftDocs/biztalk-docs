---
title: "Get Subscriptions application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: abd87fb3-bef0-43a0-b3b6-a64f6edba44a
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Subscriptions: application/json
## Get Subscriptions

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Subscriptions

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/OperationalData/Subscriptions'|
| Response Code | 200|

Response Body
---
```
[
  {
    "Id": "000cdb4b-6979-45e9-8d92-efdd46341c1b",
    "Name": "Cache: BIZTALKFP1",
    "ServiceName": "BizTalkCachingService",
    "State": "Started",
    "SubscriptionType": "InstanceSubs",
    "ServiceInstanceId": "522b325c-2677-4d17-9e6d-cd49b9b9f8de",
    "ServiceClass": "CachingService",
    "CreationTime": "2017-04-18T18:16:14.733+00:00",
    "HostName": "SendHost",
    "StartWindow": "1899-12-30T00:00:00",
    "EndWindow": "1899-12-30T00:00:00",
    "ValidTime": "1899-12-30T00:00:00+00:00",
    "OrderedDelivery": "True",
    "RequestResponse": "False",
    "Priority": 5
  },
  {
    "Id": "29f48ac8-b8fd-42e1-8192-355826319726",
    "Name": "Cache: BIZTALKFP1",
    "ServiceName": "BizTalkCachingService",
    "State": "Started",
    "SubscriptionType": "InstanceSubs",
    "ServiceInstanceId": "bc975caf-296a-49a4-845f-5e123e5bd684",
    "ServiceClass": "CachingService",
    "CreationTime": "2017-04-18T18:16:14.73+00:00",
    "HostName": "ReceiveHost",
    "StartWindow": "1899-12-30T00:00:00",
    "EndWindow": "1899-12-30T00:00:00",
    "ValidTime": "1899-12-30T00:00:00+00:00",
    "OrderedDelivery": "True",
    "RequestResponse": "False",
    "Priority": 5
  },
  {
    "Id": "98abe6e6-6341-48f0-8408-cb4c2d2c7684",
    "Name": "Cache: BIZTALKFP1",
    "ServiceName": "BizTalkCachingService",
    "State": "Started",
    "SubscriptionType": "InstanceSubs",
    "ServiceInstanceId": "e395e6e8-54fd-4555-aab8-7ba55dcaeacb",
    "ServiceClass": "CachingService",
    "CreationTime": "2017-04-18T18:16:14.73+00:00",
    "HostName": "TrackingHost",
    "StartWindow": "1899-12-30T00:00:00",
    "EndWindow": "1899-12-30T00:00:00",
    "ValidTime": "1899-12-30T00:00:00+00:00",
    "OrderedDelivery": "True",
    "RequestResponse": "False",
    "Priority": 5
  },
  {
    "Id": "e22861d0-9b22-4e4a-88ac-6754e1a8a811",
    "Name": "Cache: BIZTALKFP1",
    "ServiceName": "BizTalkCachingService",
    "State": "Started",
    "SubscriptionType": "InstanceSubs",
    "ServiceInstanceId": "193786ec-422b-4cb6-bb32-2453b327d0e6",
    "ServiceClass": "CachingService",
    "CreationTime": "2017-04-18T18:16:14.72+00:00",
    "HostName": "ProcessingHost",
    "StartWindow": "1899-12-30T00:00:00",
    "EndWindow": "1899-12-30T00:00:00",
    "ValidTime": "1899-12-30T00:00:00+00:00",
    "OrderedDelivery": "True",
    "RequestResponse": "False",
    "Priority": 5
  },
  {
    "Id": "7f74e0b2-26af-431d-be11-fee11d3ab30e",
    "Name": "Activate: AddDataToSQL.ProcessOrders(4e571b69-a081-1270-a38f-55611d0ee716)[0]",
    "ServiceName": "AddDataToSQL.ProcessOrders, OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0",
    "State": "Started",
    "SubscriptionType": "ActivationSubs",
    "ServiceInstanceId": "00000000-0000-0000-0000-000000000000",
    "ServiceClass": "Orchestration",
    "CreationTime": "2017-04-06T16:07:53.303+00:00",
    "HostName": "ProcessingHost",
    "StartWindow": "1899-12-30T00:00:00",
    "EndWindow": "1899-12-30T00:00:00",
    "ValidTime": "1899-12-30T00:00:00+00:00",
    "OrderedDelivery": "False",
    "RequestResponse": "False",
    "Priority": 7
  },
  {
    "Id": "1df2bb43-fa08-494b-9bbd-0cb5f2b1a245",
    "Name": "WcfSendPort_SqlAdapterBinding_TypedProcedures_dbo_Custom: {1DF2BB43-FA08-494B-9BBD-0CB5F2B1A245}",
    "ServiceName": "WcfSendPort_SqlAdapterBinding_TypedProcedures_dbo_Custom",
    "State": "Started",
    "SubscriptionType": "ActivationSubs",
    "ServiceInstanceId": "00000000-0000-0000-0000-000000000000",
    "ServiceClass": "Messaging",
    "CreationTime": "2017-04-06T16:07:52.21+00:00",
    "HostName": "SendHost",
    "StartWindow": "1899-12-30T00:00:00",
    "EndWindow": "1899-12-30T00:00:00",
    "ValidTime": "1899-12-30T00:00:00+00:00",
    "OrderedDelivery": "False",
    "RequestResponse": "True",
    "Priority": 5
  },
  {
    "Id": "66363be4-1d14-4bb7-9c2c-4d2a4d6c46bf",
    "Name": "BackupFile: {66363BE4-1D14-4BB7-9C2C-4D2A4D6C46BF}",
    "ServiceName": "BackupFile",
    "State": "Started",
    "SubscriptionType": "ActivationSubs",
    "ServiceInstanceId": "00000000-0000-0000-0000-000000000000",
    "ServiceClass": "Messaging",
    "CreationTime": "2017-04-06T16:07:52.187+00:00",
    "HostName": "SendHost",
    "StartWindow": "1899-12-30T00:00:00",
    "EndWindow": "1899-12-30T00:00:00",
    "ValidTime": "1899-12-30T00:00:00+00:00",
    "OrderedDelivery": "False",
    "RequestResponse": "False",
    "Priority": 5
  },
  {
    "Id": "a9756349-ab74-4fc6-afdf-dfa2c5366bd2",
    "Name": "ResponseSQL: {A9756349-AB74-4FC6-AFDF-DFA2C5366BD2}",
    "ServiceName": "ResponseSQL",
    "State": "Started",
    "SubscriptionType": "ActivationSubs",
    "ServiceInstanceId": "00000000-0000-0000-0000-000000000000",
    "ServiceClass": "Messaging",
    "CreationTime": "2017-04-06T16:07:52.16+00:00",
    "HostName": "SendHost",
    "StartWindow": "1899-12-30T00:00:00",
    "EndWindow": "1899-12-30T00:00:00",
    "ValidTime": "1899-12-30T00:00:00+00:00",
    "OrderedDelivery": "False",
    "RequestResponse": "False",
    "Priority": 5
  }
]
```


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 06:55:18 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "4296",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Id": "string",
    "Name": "string",
    "ServiceName": "string",
    "State": {},
    "SubscriptionType": {},
    "ServiceInstanceId": "string",
    "ServiceClass": {},
    "CreationTime": "2017-04-21T00:56:37.572Z",
    "HostName": "string",
    "StartWindow": "2017-04-21T00:56:37.572Z",
    "EndWindow": "2017-04-21T00:56:37.572Z",
    "ValidTime": "2017-04-21T00:56:37.572Z",
    "OrderedDelivery": "string",
    "RequestResponse": "string",
    "Priority": 0
  }
]

```
