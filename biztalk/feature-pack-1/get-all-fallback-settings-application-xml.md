---
title: "Get all fallback settings application xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 2d225e2c-4832-4332-8a54-86a160c844f2
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get all fallback settings: application/xml
## FallbackSettings

  Response Content Type: **application/xml**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/FallbackSettings


Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/xml' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/FallbackSettings'|
| Response Body | |
| Response Code | 200|

Response body
---

```
\<ArrayOfFallbackSettings xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <FallbackSettings>
    <Id>1</Id>
    <ProtocolName>x12</ProtocolName>
    <Enabled>true</Enabled>
    <ReceiverIdentity>
      <Id>2</Id>
      <Qualifier>ZZ</Qualifier>
      <Value>RECEIVE-PARTNER</Value>
    </ReceiverIdentity>
    <SenderIdentity>
      <Id>1</Id>
      <Qualifier>ZZ</Qualifier>
      <Value>BTS-SENDER</Value>
    </SenderIdentity>
    <X12FallbackProtocolSettings>
      <Id>1</Id>
      <ProtocolName>x12</ProtocolName>
      <SettingsName>""</SettingsName>
      <ValidationSettings>
        <ValidateCharacterSet>true</ValidateCharacterSet>
        <CheckDuplicateInterchangeControlNumber>false</CheckDuplicateInterchangeControlNumber>
        <InterchangeControlNumberValidityPeriod>30</InterchangeControlNumberValidityPeriod>
        <CheckDuplicateGroupControlNumber>false</CheckDuplicateGroupControlNumber>
        <CheckDuplicateTransactionSetControlNumber>false</CheckDuplicateTransactionSetControlNumber>
        <ValidateEDITypes>true</ValidateEDITypes>
        <ValidateXSDTypes>false</ValidateXSDTypes>
        <AllowLeadingAndTrailingSpacesAndZeroes>false</AllowLeadingAndTrailingSpacesAndZeroes>
        <TrimLeadingAndTrailingSpacesAndZeroes>false</TrimLeadingAndTrailingSpacesAndZeroes>
        <TrailingSeparatorPolicy>NotAllowed</TrailingSeparatorPolicy>
        <ValidationOverrides />
      </ValidationSettings>
      <FramingSettings>
        <DataElementSeparator>42</DataElementSeparator>
        <ComponentSeparator>58</ComponentSeparator>
        <ReplaceSeparatorsInPayload>false</ReplaceSeparatorsInPayload>
        <ReplaceCharacter>36</ReplaceCharacter>
        <SegmentTerminator>126</SegmentTerminator>
        <CharacterSet>UTF8</CharacterSet>
        <SegmentTerminatorSuffix>None</SegmentTerminatorSuffix>
      </FramingSettings>
      <EnvelopeSettings>
        <ControlStandardsId>85</ControlStandardsId>
        <UseControlStandardsIdAsRepetitionCharacter>false</UseControlStandardsIdAsRepetitionCharacter>
        <SenderApplicationId>BTS-SENDER</SenderApplicationId>
        <ReceiverApplicationId>RECEIVE-APP</ReceiverApplicationId>
        <ControlVersionNumber>00401</ControlVersionNumber>
        <InterchangeControlNumberLowerBound>1</InterchangeControlNumberLowerBound>
        <InterchangeControlNumberUpperBound>999999999</InterchangeControlNumberUpperBound>
        <InterchangeControlNumberRollover>true</InterchangeControlNumberRollover>
        <EnableDefaultGroupHeaders>false</EnableDefaultGroupHeaders>
        <GroupControlNumberLowerBound>1</GroupControlNumberLowerBound>
        <GroupControlNumberUpperBound>999999999</GroupControlNumberUpperBound>
        <GroupControlNumberRollover>true</GroupControlNumberRollover>
        <GroupHeaderAgencyCode>T</GroupHeaderAgencyCode>
        <GroupHeaderVersion>00401</GroupHeaderVersion>
        <TransactionSetControlNumberLowerBound>1</TransactionSetControlNumberLowerBound>
        <TransactionSetControlNumberUpperBound>999999999</TransactionSetControlNumberUpperBound>
        <TransactionSetControlNumberRollover>true</TransactionSetControlNumberRollover>
        <OverwriteExistingTransactionSetControlNumber>true</OverwriteExistingTransactionSetControlNumber>
        <GroupHeaderDateFormat>YYMMDD</GroupHeaderDateFormat>
        <GroupHeaderTimeFormat>HHMM</GroupHeaderTimeFormat>
        <UsageIndicator>Test</UsageIndicator>
        <EnvelopeOverrides />
      </EnvelopeSettings>
      <AcknowledgmentSettings>
        <NeedTechnicalAcknowledgment>false</NeedTechnicalAcknowledgment>
        <BatchTechnicalAcknowledgments>false</BatchTechnicalAcknowledgments>
        <NeedFunctionalAcknowledgment>false</NeedFunctionalAcknowledgment>
        <BatchFunctionalAcknowledgments>false</BatchFunctionalAcknowledgments>
        <NeedImplementationAcknowledgment>false</NeedImplementationAcknowledgment>
        <BatchImplementationAcknowledgments>false</BatchImplementationAcknowledgments>
        <NeedLoopForValidMessages>false</NeedLoopForValidMessages>
        <SendSynchronousAcknowledgment>true</SendSynchronousAcknowledgment>
        <AcknowledgmentControlNumberLowerBound>1</AcknowledgmentControlNumberLowerBound>
        <AcknowledgmentControlNumberUpperBound>999999999</AcknowledgmentControlNumberUpperBound>
        <AcknowledgmentControlNumberRollover>true</AcknowledgmentControlNumberRollover>
        <GeneratePatAK901>false</GeneratePatAK901>
      </AcknowledgmentSettings>
      <MessageFilter>
        <MessageFilterType>Exclude</MessageFilterType>
        <FilterMessages />
      </MessageFilter>
      <SecuritySettings>
        <AuthorizationQualifier>00</AuthorizationQualifier>
        <SecurityQualifier>00</SecurityQualifier>
      </SecuritySettings>
      <ProcessingSettings>
        <MaskSecurityInfo>true</MaskSecurityInfo>
        <ConvertImpliedDecimal>false</ConvertImpliedDecimal>
        <PreserveInterchange>false</PreserveInterchange>
        <SuspendInterchangeOnError>false</SuspendInterchangeOnError>
        <CreateEmptyXmlTagsForTrailingSeparators>true</CreateEmptyXmlTagsForTrailingSeparators>
      </ProcessingSettings>
      <SchemaSettings>
        <TargetNamespace>http://schemas.microsoft.com/BizTalk/EDI/X12/2006</TargetNamespace>
        <SchemaOverrides />
      </SchemaSettings>
    </X12FallbackProtocolSettings>
    <BizTalkHostSettings>
      <EnableStatusReporting>false</EnableStatusReporting>
      <LogErrorsToEventLog>true</LogErrorsToEventLog>
      <LogWarningsToEventLog>true</LogWarningsToEventLog>
      <StoreMessagePayload>false</StoreMessagePayload>
    </BizTalkHostSettings>
  </FallbackSettings>
  <FallbackSettings>
    <Id>2</Id>
    <ProtocolName>edifact</ProtocolName>
    <Enabled>true</Enabled>
    <ReceiverIdentity>
      <Id>4</Id>
      <Qualifier>ZZZ</Qualifier>
      <Value>RECEIVE-PARTNER</Value>
    </ReceiverIdentity>
    <SenderIdentity>
      <Id>3</Id>
      <Qualifier>ZZZ</Qualifier>
      <Value>BTS-SENDER</Value>
    </SenderIdentity>
    <EDIFACTFallbackProtocolSettings>
      <Id>2</Id>
      <ProtocolName>edifact</ProtocolName>
      <SettingsName>""</SettingsName>
      <ValidationSettings>
        <ValidateCharacterSet>true</ValidateCharacterSet>
        <CheckDuplicateInterchangeControlNumber>false</CheckDuplicateInterchangeControlNumber>
        <InterchangeControlNumberValidityPeriod>30</InterchangeControlNumberValidityPeriod>
        <CheckDuplicateGroupControlNumber>false</CheckDuplicateGroupControlNumber>
        <CheckDuplicateTransactionSetControlNumber>false</CheckDuplicateTransactionSetControlNumber>
        <ValidateEDITypes>true</ValidateEDITypes>
        <ValidateXSDTypes>false</ValidateXSDTypes>
        <AllowLeadingAndTrailingSpacesAndZeroes>false</AllowLeadingAndTrailingSpacesAndZeroes>
        <TrimLeadingAndTrailingSpacesAndZeroes>false</TrimLeadingAndTrailingSpacesAndZeroes>
        <TrailingSeparatorPolicy>NotAllowed</TrailingSeparatorPolicy>
        <ValidationOverrides />
      </ValidationSettings>
      <FramingSettings>
        <ProtocolVersion>1</ProtocolVersion>
        <DataElementSeparator>43</DataElementSeparator>
        <ComponentSeparator>58</ComponentSeparator>
        <SegmentTerminator>39</SegmentTerminator>
        <ReleaseIndicator>63</ReleaseIndicator>
        <RepetitionSeparator>42</RepetitionSeparator>
        <CharacterSet>UNOB</CharacterSet>
        <DecimalPointIndicator>Comma</DecimalPointIndicator>
        <SegmentTerminatorSuffix>None</SegmentTerminatorSuffix>
      </FramingSettings>
      <EnvelopeSettings>
        <ApplyDelimiterStringAdvice>false</ApplyDelimiterStringAdvice>
        <CommunicationAgreementId />
        <CreateGroupingSegments>false</CreateGroupingSegments>
        <IsTestInterchange>false</IsTestInterchange>
        <ProcessingPriorityCode />
        <InterchangeControlNumberLowerBound>1</InterchangeControlNumberLowerBound>
        <InterchangeControlNumberUpperBound>99999999999999</InterchangeControlNumberUpperBound>
        <InterchangeControlNumberRollover>false</InterchangeControlNumberRollover>
        <EnableDefaultGroupHeaders>false</EnableDefaultGroupHeaders>
        <GroupControlNumberLowerBound>1</GroupControlNumberLowerBound>
        <GroupControlNumberUpperBound>99999999999999</GroupControlNumberUpperBound>
        <GroupControlNumberRollover>false</GroupControlNumberRollover>
        <TransactionSetControlNumberLowerBound>1</TransactionSetControlNumberLowerBound>
        <TransactionSetControlNumberUpperBound>99999999999999</TransactionSetControlNumberUpperBound>
        <TransactionSetControlNumberRollover>true</TransactionSetControlNumberRollover>
        <OverwriteExistingTransactionSetControlNumber>true</OverwriteExistingTransactionSetControlNumber>
        <EnvelopeOverrides />
      </EnvelopeSettings>
      <AcknowledgmentSettings>
        <NeedTechnicalAcknowledgment>false</NeedTechnicalAcknowledgment>
        <BatchTechnicalAcknowledgments>false</BatchTechnicalAcknowledgments>
        <NeedFunctionalAcknowledgment>false</NeedFunctionalAcknowledgment>
        <BatchFunctionalAcknowledgments>false</BatchFunctionalAcknowledgments>
        <NeedLoopForValidMessages>false</NeedLoopForValidMessages>
        <SendSynchronousAcknowledgment>true</SendSynchronousAcknowledgment>
        <AcknowledgmentControlNumberLowerBound>1</AcknowledgmentControlNumberLowerBound>
        <AcknowledgmentControlNumberUpperBound>99999999999999</AcknowledgmentControlNumberUpperBound>
        <AcknowledgmentControlNumberRollover>true</AcknowledgmentControlNumberRollover>
      </AcknowledgmentSettings>
      <MessageFilter>
        <MessageFilterType>Exclude</MessageFilterType>
        <FilterMessages />
      </MessageFilter>
      <ProcessingSettings>
        <MaskSecurityInfo>true</MaskSecurityInfo>
        <PreserveInterchange>false</PreserveInterchange>
        <SuspendInterchangeOnError>false</SuspendInterchangeOnError>
        <CreateEmptyXmlTagsForTrailingSeparators>true</CreateEmptyXmlTagsForTrailingSeparators>
        <UseDotAsDecimalSeparator>true</UseDotAsDecimalSeparator>
      </ProcessingSettings>
      <SchemaSettings>
        <TargetNamespace>http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006</TargetNamespace>
        <SchemaOverrides />
      </SchemaSettings>
      <IsTestInterchange>false</IsTestInterchange>
    </EDIFACTFallbackProtocolSettings>
    <BizTalkHostSettings>
      <EnableStatusReporting>false</EnableStatusReporting>
      <LogErrorsToEventLog>true</LogErrorsToEventLog>
      <LogWarningsToEventLog>true</LogWarningsToEventLog>
      <StoreMessagePayload>false</StoreMessagePayload>
    </BizTalkHostSettings>
  </FallbackSettings>
</ArrayOfFallbackSettings>
```

Response Headers
---


```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 07:24:23 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/xml; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "9225",
  "expires": "-1"
}
```


Example Value
---

```
\<?xml version="1.0"?>
<Inline Model>
  <Id>1</Id>
  <ProtocolName>string</ProtocolName>
  <Enabled>true</Enabled>
  <ReceiverIdentity>
    <Description>string</Description>
    <Qualifier>string</Qualifier>
    <Value>string</Value>
    <Id>1</Id>
  </ReceiverIdentity>
  <SenderIdentity>
    <Description>string</Description>
    <Qualifier>string</Qualifier>
    <Value>string</Value>
    <Id>1</Id>
  </SenderIdentity>
  <X12FallbackProtocolSettings>
    <ValidationSettings>
      <ValidateCharacterSet>true</ValidateCharacterSet>
      <CheckDuplicateInterchangeControlNumber>true</CheckDuplicateInterchangeControlNumber>
      <InterchangeControlNumberValidityPeriod>1</InterchangeControlNumberValidityPeriod>
      <CheckDuplicateGroupControlNumber>true</CheckDuplicateGroupControlNumber>
      <CheckDuplicateTransactionSetControlNumber>true</CheckDuplicateTransactionSetControlNumber>
      <ValidateEDITypes>true</ValidateEDITypes>
      <ValidateXSDTypes>true</ValidateXSDTypes>
      <AllowLeadingAndTrailingSpacesAndZeroes>true</AllowLeadingAndTrailingSpacesAndZeroes>
      <TrimLeadingAndTrailingSpacesAndZeroes>true</TrimLeadingAndTrailingSpacesAndZeroes>
      <TrailingSeparatorPolicy>string</TrailingSeparatorPolicy>
      <ValidationOverrides>
        <MessageId>string</MessageId>
        <ValidateEDITypes>true</ValidateEDITypes>
        <ValidateXSDTypes>true</ValidateXSDTypes>
        <AllowLeadingAndTrailingSpacesAndZeroes>true</AllowLeadingAndTrailingSpacesAndZeroes>
        <ValidateCharacterSet>true</ValidateCharacterSet>
        <TrimLeadingAndTrailingSpacesAndZeroes>true</TrimLeadingAndTrailingSpacesAndZeroes>
        <TrailingSeparatorPolicy>string</TrailingSeparatorPolicy>
      </ValidationOverrides>
    </ValidationSettings>
    <FramingSettings>
      <DataElementSeparator>1</DataElementSeparator>
      <ComponentSeparator>1</ComponentSeparator>
      <ReplaceSeparatorsInPayload>true</ReplaceSeparatorsInPayload>
      <ReplaceCharacter>1</ReplaceCharacter>
      <SegmentTerminator>1</SegmentTerminator>
      <CharacterSet>string</CharacterSet>
      <SegmentTerminatorSuffix>string</SegmentTerminatorSuffix>
    </FramingSettings>
    <EnvelopeSettings>
      <ControlStandardsId>1</ControlStandardsId>
      <UseControlStandardsIdAsRepetitionCharacter>true</UseControlStandardsIdAsRepetitionCharacter>
      <SenderApplicationId>string</SenderApplicationId>
      <ReceiverApplicationId>string</ReceiverApplicationId>
      <ControlVersionNumber>string</ControlVersionNumber>
      <InterchangeControlNumberLowerBound>1</InterchangeControlNumberLowerBound>
      <InterchangeControlNumberUpperBound>1</InterchangeControlNumberUpperBound>
      <InterchangeControlNumberRollover>true</InterchangeControlNumberRollover>
      <EnableDefaultGroupHeaders>true</EnableDefaultGroupHeaders>
      <FunctionalGroupId>string</FunctionalGroupId>
      <GroupControlNumberLowerBound>1</GroupControlNumberLowerBound>
      <GroupControlNumberUpperBound>1</GroupControlNumberUpperBound>
      <GroupControlNumberRollover>true</GroupControlNumberRollover>
      <GroupHeaderAgencyCode>string</GroupHeaderAgencyCode>
      <GroupHeaderVersion>string</GroupHeaderVersion>
      <TransactionSetControlNumberLowerBound>1</TransactionSetControlNumberLowerBound>
      <TransactionSetControlNumberUpperBound>1</TransactionSetControlNumberUpperBound>
      <TransactionSetControlNumberRollover>true</TransactionSetControlNumberRollover>
      <TransactionSetControlNumberPrefix>string</TransactionSetControlNumberPrefix>
      <TransactionSetControlNumberSuffix>string</TransactionSetControlNumberSuffix>
      <OverwriteExistingTransactionSetControlNumber>true</OverwriteExistingTransactionSetControlNumber>
      <GroupHeaderDateFormat>string</GroupHeaderDateFormat>
      <GroupHeaderTimeFormat>string</GroupHeaderTimeFormat>
      <UsageIndicator>string</UsageIndicator>
      <EnvelopeOverrides>
        <TargetNamespace>string</TargetNamespace>
        <TargetNamespaceString>string</TargetNamespaceString>
        <ProtocolVersion>string</ProtocolVersion>
        <MessageId>string</MessageId>
        <ResponsibleAgencyCode>string</ResponsibleAgencyCode>
        <HeaderVersion>string</HeaderVersion>
        <SenderApplicationId>string</SenderApplicationId>
        <ReceiverApplicationId>string</ReceiverApplicationId>
        <FunctionalIdentifierCode>string</FunctionalIdentifierCode>
        <DateFormat>string</DateFormat>
        <TimeFormat>string</TimeFormat>
      </EnvelopeOverrides>
    </EnvelopeSettings>
    <AcknowledgmentSettings>
      <NeedTechnicalAcknowledgment>true</NeedTechnicalAcknowledgment>
      <BatchTechnicalAcknowledgments>true</BatchTechnicalAcknowledgments>
      <NeedFunctionalAcknowledgment>true</NeedFunctionalAcknowledgment>
      <FunctionalAcknowledgmentVersion>string</FunctionalAcknowledgmentVersion>
      <BatchFunctionalAcknowledgments>true</BatchFunctionalAcknowledgments>
      <NeedImplementationAcknowledgment>true</NeedImplementationAcknowledgment>
      <ImplementationAcknowledgmentVersion>string</ImplementationAcknowledgmentVersion>
      <BatchImplementationAcknowledgments>true</BatchImplementationAcknowledgments>
      <NeedLoopForValidMessages>true</NeedLoopForValidMessages>
      <SendSynchronousAcknowledgment>true</SendSynchronousAcknowledgment>
      <AcknowledgmentControlNumberPrefix>string</AcknowledgmentControlNumberPrefix>
      <AcknowledgmentControlNumberSuffix>string</AcknowledgmentControlNumberSuffix>
      <AcknowledgmentControlNumberLowerBound>1</AcknowledgmentControlNumberLowerBound>
      <AcknowledgmentControlNumberUpperBound>1</AcknowledgmentControlNumberUpperBound>
      <AcknowledgmentControlNumberRollover>true</AcknowledgmentControlNumberRollover>
      <GeneratePatAK901>true</GeneratePatAK901>
    </AcknowledgmentSettings>
    <MessageFilter>
      <MessageFilterType>string</MessageFilterType>
      <FilterMessages>
        <MessageId>string</MessageId>
      </FilterMessages>
    </MessageFilter>
    <SecuritySettings>
      <AuthorizationQualifier>string</AuthorizationQualifier>
      <AuthorizationValue>string</AuthorizationValue>
      <SecurityQualifier>string</SecurityQualifier>
      <PasswordValue>string</PasswordValue>
    </SecuritySettings>
    <ProcessingSettings>
      <MaskSecurityInfo>true</MaskSecurityInfo>
      <ConvertImpliedDecimal>true</ConvertImpliedDecimal>
      <PreserveInterchange>true</PreserveInterchange>
      <SuspendInterchangeOnError>true</SuspendInterchangeOnError>
      <CreateEmptyXmlTagsForTrailingSeparators>true</CreateEmptyXmlTagsForTrailingSeparators>
    </ProcessingSettings>
    <SchemaSettings>
      <TargetNamespace>string</TargetNamespace>
      <SchemaOverrides>
        <MessageId>string</MessageId>
        <SenderApplicationId>string</SenderApplicationId>
        <TargetNamespace>string</TargetNamespace>
      </SchemaOverrides>
    </SchemaSettings>
    <Id>1</Id>
    <ProtocolName>string</ProtocolName>
    <SettingsName>string</SettingsName>
  </X12FallbackProtocolSettings>
  <EDIFACTFallbackProtocolSettings>
    <ValidationSettings>
      <ValidateCharacterSet>true</ValidateCharacterSet>
      <CheckDuplicateInterchangeControlNumber>true</CheckDuplicateInterchangeControlNumber>
      <InterchangeControlNumberValidityPeriod>1</InterchangeControlNumberValidityPeriod>
      <CheckDuplicateGroupControlNumber>true</CheckDuplicateGroupControlNumber>
      <CheckDuplicateTransactionSetControlNumber>true</CheckDuplicateTransactionSetControlNumber>
      <ValidateEDITypes>true</ValidateEDITypes>
      <ValidateXSDTypes>true</ValidateXSDTypes>
      <AllowLeadingAndTrailingSpacesAndZeroes>true</AllowLeadingAndTrailingSpacesAndZeroes>
      <TrimLeadingAndTrailingSpacesAndZeroes>true</TrimLeadingAndTrailingSpacesAndZeroes>
      <TrailingSeparatorPolicy>string</TrailingSeparatorPolicy>
      <ValidationOverrides>
        <MessageId>string</MessageId>
        <ValidateEDITypes>true</ValidateEDITypes>
        <ValidateXSDTypes>true</ValidateXSDTypes>
        <AllowLeadingAndTrailingSpacesAndZeroes>true</AllowLeadingAndTrailingSpacesAndZeroes>
        <EnforceCharacterSet>true</EnforceCharacterSet>
        <TrimLeadingAndTrailingSpacesAndZeroes>true</TrimLeadingAndTrailingSpacesAndZeroes>
        <TrailingSeparatorPolicy>string</TrailingSeparatorPolicy>
        <InternalTrailingSeparatorPolicy>1</InternalTrailingSeparatorPolicy>
      </ValidationOverrides>
    </ValidationSettings>
    <FramingSettings>
      <ServiceCodeListDirectoryVersion>string</ServiceCodeListDirectoryVersion>
      <CharacterEncoding>string</CharacterEncoding>
      <ProtocolVersion>1</ProtocolVersion>
      <DataElementSeparator>1</DataElementSeparator>
      <ComponentSeparator>1</ComponentSeparator>
      <SegmentTerminator>1</SegmentTerminator>
      <ReleaseIndicator>1</ReleaseIndicator>
      <RepetitionSeparator>1</RepetitionSeparator>
      <CharacterSet>string</CharacterSet>
      <DecimalPointIndicator>string</DecimalPointIndicator>
      <SegmentTerminatorSuffix>string</SegmentTerminatorSuffix>
    </FramingSettings>
    <EnvelopeSettings>
      <ApplicationReferenceId>string</ApplicationReferenceId>
      <ApplyDelimiterStringAdvice>true</ApplyDelimiterStringAdvice>
      <CommunicationAgreementId>string</CommunicationAgreementId>
      <CreateGroupingSegments>true</CreateGroupingSegments>
      <GroupApplicationPassword>string</GroupApplicationPassword>
      <GroupApplicationReceiverId>string</GroupApplicationReceiverId>
      <GroupApplicationReceiverQualifier>string</GroupApplicationReceiverQualifier>
      <GroupApplicationSenderId>string</GroupApplicationSenderId>
      <GroupApplicationSenderQualifier>string</GroupApplicationSenderQualifier>
      <GroupAssociationAssignedCode>string</GroupAssociationAssignedCode>
      <GroupControllingAgencyCode>string</GroupControllingAgencyCode>
      <GroupControlNumberPrefix>string</GroupControlNumberPrefix>
      <GroupControlNumberSuffix>string</GroupControlNumberSuffix>
      <GroupMessageRelease>string</GroupMessageRelease>
      <GroupMessageVersion>string</GroupMessageVersion>
      <InterchangeControlNumberPrefix>string</InterchangeControlNumberPrefix>
      <InterchangeControlNumberSuffix>string</InterchangeControlNumberSuffix>
      <IsTestInterchange>true</IsTestInterchange>
      <ProcessingPriorityCode>string</ProcessingPriorityCode>
      <ReceiverInternalIdentification>string</ReceiverInternalIdentification>
      <ReceiverInternalSubIdentification>string</ReceiverInternalSubIdentification>
      <ReceiverReverseRoutingAddress>string</ReceiverReverseRoutingAddress>
      <RecipientReferencePasswordQualifier>string</RecipientReferencePasswordQualifier>
      <RecipientReferencePasswordValue>string</RecipientReferencePasswordValue>
      <SenderInternalIdentification>string</SenderInternalIdentification>
      <SenderInternalSubIdentification>string</SenderInternalSubIdentification>
      <SenderReverseRoutingAddress>string</SenderReverseRoutingAddress>
      <InterchangeControlNumberLowerBound>1</InterchangeControlNumberLowerBound>
      <InterchangeControlNumberUpperBound>1</InterchangeControlNumberUpperBound>
      <InterchangeControlNumberRollover>true</InterchangeControlNumberRollover>
      <EnableDefaultGroupHeaders>true</EnableDefaultGroupHeaders>
      <FunctionalGroupId>string</FunctionalGroupId>
      <GroupControlNumberLowerBound>1</GroupControlNumberLowerBound>
      <GroupControlNumberUpperBound>1</GroupControlNumberUpperBound>
      <GroupControlNumberRollover>true</GroupControlNumberRollover>
      <TransactionSetControlNumberLowerBound>1</TransactionSetControlNumberLowerBound>
      <TransactionSetControlNumberUpperBound>1</TransactionSetControlNumberUpperBound>
      <TransactionSetControlNumberRollover>true</TransactionSetControlNumberRollover>
      <TransactionSetControlNumberPrefix>string</TransactionSetControlNumberPrefix>
      <TransactionSetControlNumberSuffix>string</TransactionSetControlNumberSuffix>
      <OverwriteExistingTransactionSetControlNumber>true</OverwriteExistingTransactionSetControlNumber>
      <EnvelopeOverrides>
        <MessageId>string</MessageId>
        <MessageVersion>string</MessageVersion>
        <MessageRelease>string</MessageRelease>
        <MessageAssociationAssignedCode>string</MessageAssociationAssignedCode>
        <TargetNamespace>string</TargetNamespace>
        <FunctionalGroupId>string</FunctionalGroupId>
        <SenderApplicationQualifier>string</SenderApplicationQualifier>
        <SenderApplicationId>string</SenderApplicationId>
        <ReceiverApplicationQualifier>string</ReceiverApplicationQualifier>
        <ReceiverApplicationId>string</ReceiverApplicationId>
        <ControllingAgencyCode>string</ControllingAgencyCode>
        <GroupHeaderMessageVersion>string</GroupHeaderMessageVersion>
        <GroupHeaderMessageRelease>string</GroupHeaderMessageRelease>
        <AssociationAssignedCode>string</AssociationAssignedCode>
        <ApplicationPassword>string</ApplicationPassword>
      </EnvelopeOverrides>
    </EnvelopeSettings>
    <AcknowledgmentSettings>
      <NeedTechnicalAcknowledgment>true</NeedTechnicalAcknowledgment>
      <BatchTechnicalAcknowledgments>true</BatchTechnicalAcknowledgments>
      <NeedFunctionalAcknowledgment>true</NeedFunctionalAcknowledgment>
      <BatchFunctionalAcknowledgments>true</BatchFunctionalAcknowledgments>
      <NeedLoopForValidMessages>true</NeedLoopForValidMessages>
      <SendSynchronousAcknowledgment>true</SendSynchronousAcknowledgment>
      <AcknowledgmentControlNumberPrefix>string</AcknowledgmentControlNumberPrefix>
      <AcknowledgmentControlNumberSuffix>string</AcknowledgmentControlNumberSuffix>
      <AcknowledgmentControlNumberLowerBound>1</AcknowledgmentControlNumberLowerBound>
      <AcknowledgmentControlNumberUpperBound>1</AcknowledgmentControlNumberUpperBound>
      <AcknowledgmentControlNumberRollover>true</AcknowledgmentControlNumberRollover>
    </AcknowledgmentSettings>
    <MessageFilter>
      <MessageFilterType>string</MessageFilterType>
      <FilterMessages>
        <MessageId>string</MessageId>
      </FilterMessages>
    </MessageFilter>
    <ProcessingSettings>
      <MaskSecurityInfo>true</MaskSecurityInfo>
      <PreserveInterchange>true</PreserveInterchange>
      <SuspendInterchangeOnError>true</SuspendInterchangeOnError>
      <CreateEmptyXmlTagsForTrailingSeparators>true</CreateEmptyXmlTagsForTrailingSeparators>
      <UseDotAsDecimalSeparator>true</UseDotAsDecimalSeparator>
    </ProcessingSettings>
    <SchemaSettings>
      <TargetNamespace>string</TargetNamespace>
      <SchemaOverrides>
        <MessageId>string</MessageId>
        <MessageVersion>string</MessageVersion>
        <MessageRelease>string</MessageRelease>
        <ApplicationSenderID>string</ApplicationSenderID>
        <ApplicationSenderQualifier>string</ApplicationSenderQualifier>
        <AssociationAssignedCode>string</AssociationAssignedCode>
        <TargetNamespace>string</TargetNamespace>
      </SchemaOverrides>
    </SchemaSettings>
    <IsTestInterchange>true</IsTestInterchange>
    <Id>1</Id>
    <ProtocolName>string</ProtocolName>
    <SettingsName>string</SettingsName>
  </EDIFACTFallbackProtocolSettings>
  <BizTalkHostSettings>
    <EnableStatusReporting>true</EnableStatusReporting>
    <LogErrorsToEventLog>true</LogErrorsToEventLog>
    <LogWarningsToEventLog>true</LogWarningsToEventLog>
    <StoreMessagePayload>true</StoreMessagePayload>
  </BizTalkHostSettings>
\</Inline Model>
```