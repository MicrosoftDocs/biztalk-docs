---
title: "Get batches from one party to another text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: cb97c5bc-180e-4a7c-994e-299b32425b91
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get batches from one party to another: text/xml
## Get batches from one party to another

  Response Content Type: **text/xml**

Request
---
Response Class (Status 200)

OK


Parameters
---

Parameter|Value |Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
senderParty|(required)|The sender of the agreement.|path|string|
receiverParty|(required)|The receiver of the agreement.|path|string|
agreementName|(required)|The agreement name.|path|string|


Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
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
\</Inline Model>
```