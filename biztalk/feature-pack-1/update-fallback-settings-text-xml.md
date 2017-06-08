---
title: "Update fallback settings text xml | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: 66ae7091-ea84-4a61-a3c8-7e47c5cf3eaf
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update fallback settings: text/xml
## Update fallback settings

  Response Content Type: **text/xml**
  
Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/FallbackSettings

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Content-Type: text/xml' --header 'Accept: text/plain' -d 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/FallbackSettings'|
| Response Body |Invalid protocol: string.|
| Response Code |404|


Parameters
---


Parameter|Value|Description|Parameter Type|Data Type  
---------|---------|---------|---------|---------
fallbackSettings|(required)|The fallback settings.|body | |         



Response Messages
---

HTTP Status Code|Reason|Response Model|Headers  
---------|---------|---------|---------
204     |No Content  |         |       |  

Response headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 07:55:38 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/plain; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "25",
  "expires": "-1"
}
```
Example Value
---

```
\<?xml version="1.0"?>
<FallbackSettings>
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
</FallbackSettings>
```