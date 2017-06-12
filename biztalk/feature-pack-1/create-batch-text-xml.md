---
title: "Create batch. text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: ea743563-cc06-4257-a4e1-9c68e0ae24ac
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create batch.: text/xml
## Create batch.

  Response Content Type: **text/xml**

Parameters
---


Parameter|Value |Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
batchDescription|(required)|The batch description.|body| |
senderParty|(required)|The sender of the agreement.|path|string|
receiverParty|(required)|The receiver of the agreement.|path|string|
|agreementName|(required)|The agreement name.|path|string|

Example Value
---

```
\<?xml version="1.0"?>
<BatchDescription>
  <Id>1</Id>
  <Name>string</Name>
  <Description>string</Description>
  <Protocol>string</Protocol>
  <StartDate>1970-01-01T00:00:00.001Z</StartDate>
  <EndDate>1970-01-01T00:00:00.001Z</EndDate>
  <TerminationCount>1</TerminationCount>
  <Filter>
    <Groups>
      <Statements>
        <Property>string</Property>
        <Operator>string</Operator>
        <Value>string</Value>
      </Statements>
    </Groups>
  </Filter>
  <MessageCountRelease>
    <MessageScope>string</MessageScope>
    <MessageCount>1</MessageCount>
  </MessageCountRelease>
  <ManualRelease></ManualRelease>
  <InterchangeSizeRelease>
    <CharacterCount>1</CharacterCount>
  </InterchangeSizeRelease>
  <TimeBasedRelease>
    <WeeklyRecurrence>
      <WeekDays>string</WeekDays>
      <RecurrencePeriod>string</RecurrencePeriod>
    </WeeklyRecurrence>
    <HourlyRecurrence>
      <Hours>1</Hours>
      <Minutes>1</Minutes>
      <RecurrencePeriod>string</RecurrencePeriod>
    </HourlyRecurrence>
    <DailyRecurrence>
      <Days>1</Days>
      <RecurrencePeriod>string</RecurrencePeriod>
    </DailyRecurrence>
    <FirstRelease>1970-01-01T00:00:00.001Z</FirstRelease>
    <SendEmptyBatchSignal>true</SendEmptyBatchSignal>
  </TimeBasedRelease>
</BatchDescription>

```

Response Messages
---



HTTP Status Code|Reason|Response Model|Headers  
---------|---------|---------|---------
204     |No Content  |         |        | 

