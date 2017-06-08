---
title: "Update fallback settings text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: f23a9a06-26ae-4141-8ee1-d0c63ff66e40
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update fallback settings: text/json
## Update fallback settings

  Response Content Type: **text/json**
  
Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/FallbackSettings

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X PUT --header 'Content-Type: text/json' --header 'Accept: text/plain' -d 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/FallbackSettings'|
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
{
  "Id": 0,
  "ProtocolName": "string",
  "Enabled": true,
  "ReceiverIdentity": {
    "Description": "string",
    "Qualifier": "string",
    "Value": "string",
    "Id": 0
  },
  "SenderIdentity": {
    "Description": "string",
    "Qualifier": "string",
    "Value": "string",
    "Id": 0
  },
  "X12FallbackProtocolSettings": {
    "ValidationSettings": {
      "ValidateCharacterSet": true,
      "CheckDuplicateInterchangeControlNumber": true,
      "InterchangeControlNumberValidityPeriod": 0,
      "CheckDuplicateGroupControlNumber": true,
      "CheckDuplicateTransactionSetControlNumber": true,
      "ValidateEDITypes": true,
      "ValidateXSDTypes": true,
      "AllowLeadingAndTrailingSpacesAndZeroes": true,
      "TrimLeadingAndTrailingSpacesAndZeroes": true,
      "TrailingSeparatorPolicy": "string",
      "ValidationOverrides": [
        {
          "MessageId": "string",
          "ValidateEDITypes": true,
          "ValidateXSDTypes": true,
          "AllowLeadingAndTrailingSpacesAndZeroes": true,
          "ValidateCharacterSet": true,
          "TrimLeadingAndTrailingSpacesAndZeroes": true,
          "TrailingSeparatorPolicy": "string"
        }
      ]
    },
    "FramingSettings": {
      "DataElementSeparator": 0,
      "ComponentSeparator": 0,
      "ReplaceSeparatorsInPayload": true,
      "ReplaceCharacter": 0,
      "SegmentTerminator": 0,
      "CharacterSet": "string",
      "SegmentTerminatorSuffix": "string"
    },
    "EnvelopeSettings": {
      "ControlStandardsId": 0,
      "UseControlStandardsIdAsRepetitionCharacter": true,
      "SenderApplicationId": "string",
      "ReceiverApplicationId": "string",
      "ControlVersionNumber": "string",
      "InterchangeControlNumberLowerBound": 0,
      "InterchangeControlNumberUpperBound": 0,
      "InterchangeControlNumberRollover": true,
      "EnableDefaultGroupHeaders": true,
      "FunctionalGroupId": "string",
      "GroupControlNumberLowerBound": 0,
      "GroupControlNumberUpperBound": 0,
      "GroupControlNumberRollover": true,
      "GroupHeaderAgencyCode": "string",
      "GroupHeaderVersion": "string",
      "TransactionSetControlNumberLowerBound": 0,
      "TransactionSetControlNumberUpperBound": 0,
      "TransactionSetControlNumberRollover": true,
      "TransactionSetControlNumberPrefix": "string",
      "TransactionSetControlNumberSuffix": "string",
      "OverwriteExistingTransactionSetControlNumber": true,
      "GroupHeaderDateFormat": "string",
      "GroupHeaderTimeFormat": "string",
      "UsageIndicator": "string",
      "EnvelopeOverrides": [
        {
          "TargetNamespace": "string",
          "TargetNamespaceString": "string",
          "ProtocolVersion": "string",
          "MessageId": "string",
          "ResponsibleAgencyCode": "string",
          "HeaderVersion": "string",
          "SenderApplicationId": "string",
          "ReceiverApplicationId": "string",
          "FunctionalIdentifierCode": "string",
          "DateFormat": "string",
          "TimeFormat": "string"
        }
      ]
    },
    "AcknowledgmentSettings": {
      "NeedTechnicalAcknowledgment": true,
      "BatchTechnicalAcknowledgments": true,
      "NeedFunctionalAcknowledgment": true,
      "FunctionalAcknowledgmentVersion": "string",
      "BatchFunctionalAcknowledgments": true,
      "NeedImplementationAcknowledgment": true,
      "ImplementationAcknowledgmentVersion": "string",
      "BatchImplementationAcknowledgments": true,
      "NeedLoopForValidMessages": true,
      "SendSynchronousAcknowledgment": true,
      "AcknowledgmentControlNumberPrefix": "string",
      "AcknowledgmentControlNumberSuffix": "string",
      "AcknowledgmentControlNumberLowerBound": 0,
      "AcknowledgmentControlNumberUpperBound": 0,
      "AcknowledgmentControlNumberRollover": true,
      "GeneratePatAK901": true
    },
    "MessageFilter": {
      "MessageFilterType": "string",
      "FilterMessages": [
        {
          "MessageId": "string"
        }
      ]
    },
    "SecuritySettings": {
      "AuthorizationQualifier": "string",
      "AuthorizationValue": "string",
      "SecurityQualifier": "string",
      "PasswordValue": "string"
    },
    "ProcessingSettings": {
      "MaskSecurityInfo": true,
      "ConvertImpliedDecimal": true,
      "PreserveInterchange": true,
      "SuspendInterchangeOnError": true,
      "CreateEmptyXmlTagsForTrailingSeparators": true
    },
    "SchemaSettings": {
      "TargetNamespace": "string",
      "SchemaOverrides": [
        {
          "MessageId": "string",
          "SenderApplicationId": "string",
          "TargetNamespace": "string"
        }
      ]
    },
    "Id": 0,
    "ProtocolName": "string",
    "SettingsName": "string"
  },
  "EDIFACTFallbackProtocolSettings": {
    "ValidationSettings": {
      "ValidateCharacterSet": true,
      "CheckDuplicateInterchangeControlNumber": true,
      "InterchangeControlNumberValidityPeriod": 0,
      "CheckDuplicateGroupControlNumber": true,
      "CheckDuplicateTransactionSetControlNumber": true,
      "ValidateEDITypes": true,
      "ValidateXSDTypes": true,
      "AllowLeadingAndTrailingSpacesAndZeroes": true,
      "TrimLeadingAndTrailingSpacesAndZeroes": true,
      "TrailingSeparatorPolicy": "string",
      "ValidationOverrides": [
        {
          "MessageId": "string",
          "ValidateEDITypes": true,
          "ValidateXSDTypes": true,
          "AllowLeadingAndTrailingSpacesAndZeroes": true,
          "EnforceCharacterSet": true,
          "TrimLeadingAndTrailingSpacesAndZeroes": true,
          "TrailingSeparatorPolicy": "string",
          "InternalTrailingSeparatorPolicy": 0
        }
      ]
    },
    "FramingSettings": {
      "ServiceCodeListDirectoryVersion": "string",
      "CharacterEncoding": "string",
      "ProtocolVersion": 0,
      "DataElementSeparator": 0,
      "ComponentSeparator": 0,
      "SegmentTerminator": 0,
      "ReleaseIndicator": 0,
      "RepetitionSeparator": 0,
      "CharacterSet": "string",
      "DecimalPointIndicator": "string",
      "SegmentTerminatorSuffix": "string"
    },
    "EnvelopeSettings": {
      "ApplicationReferenceId": "string",
      "ApplyDelimiterStringAdvice": true,
      "CommunicationAgreementId": "string",
      "CreateGroupingSegments": true,
      "GroupApplicationPassword": "string",
      "GroupApplicationReceiverId": "string",
      "GroupApplicationReceiverQualifier": "string",
      "GroupApplicationSenderId": "string",
      "GroupApplicationSenderQualifier": "string",
      "GroupAssociationAssignedCode": "string",
      "GroupControllingAgencyCode": "string",
      "GroupControlNumberPrefix": "string",
      "GroupControlNumberSuffix": "string",
      "GroupMessageRelease": "string",
      "GroupMessageVersion": "string",
      "InterchangeControlNumberPrefix": "string",
      "InterchangeControlNumberSuffix": "string",
      "IsTestInterchange": true,
      "ProcessingPriorityCode": "string",
      "ReceiverInternalIdentification": "string",
      "ReceiverInternalSubIdentification": "string",
      "ReceiverReverseRoutingAddress": "string",
      "RecipientReferencePasswordQualifier": "string",
      "RecipientReferencePasswordValue": "string",
      "SenderInternalIdentification": "string",
      "SenderInternalSubIdentification": "string",
      "SenderReverseRoutingAddress": "string",
      "InterchangeControlNumberLowerBound": 0,
      "InterchangeControlNumberUpperBound": 0,
      "InterchangeControlNumberRollover": true,
      "EnableDefaultGroupHeaders": true,
      "FunctionalGroupId": "string",
      "GroupControlNumberLowerBound": 0,
      "GroupControlNumberUpperBound": 0,
      "GroupControlNumberRollover": true,
      "TransactionSetControlNumberLowerBound": 0,
      "TransactionSetControlNumberUpperBound": 0,
      "TransactionSetControlNumberRollover": true,
      "TransactionSetControlNumberPrefix": "string",
      "TransactionSetControlNumberSuffix": "string",
      "OverwriteExistingTransactionSetControlNumber": true,
      "EnvelopeOverrides": [
        {
          "MessageId": "string",
          "MessageVersion": "string",
          "MessageRelease": "string",
          "MessageAssociationAssignedCode": "string",
          "TargetNamespace": "string",
          "FunctionalGroupId": "string",
          "SenderApplicationQualifier": "string",
          "SenderApplicationId": "string",
          "ReceiverApplicationQualifier": "string",
          "ReceiverApplicationId": "string",
          "ControllingAgencyCode": "string",
          "GroupHeaderMessageVersion": "string",
          "GroupHeaderMessageRelease": "string",
          "AssociationAssignedCode": "string",
          "ApplicationPassword": "string"
        }
      ]
    },
    "AcknowledgmentSettings": {
      "NeedTechnicalAcknowledgment": true,
      "BatchTechnicalAcknowledgments": true,
      "NeedFunctionalAcknowledgment": true,
      "BatchFunctionalAcknowledgments": true,
      "NeedLoopForValidMessages": true,
      "SendSynchronousAcknowledgment": true,
      "AcknowledgmentControlNumberPrefix": "string",
      "AcknowledgmentControlNumberSuffix": "string",
      "AcknowledgmentControlNumberLowerBound": 0,
      "AcknowledgmentControlNumberUpperBound": 0,
      "AcknowledgmentControlNumberRollover": true
    },
    "MessageFilter": {
      "MessageFilterType": "string",
      "FilterMessages": [
        {
          "MessageId": "string"
        }
      ]
    },
    "ProcessingSettings": {
      "MaskSecurityInfo": true,
      "PreserveInterchange": true,
      "SuspendInterchangeOnError": true,
      "CreateEmptyXmlTagsForTrailingSeparators": true,
      "UseDotAsDecimalSeparator": true
    },
    "SchemaSettings": {
      "TargetNamespace": "string",
      "SchemaOverrides": [
        {
          "MessageId": "string",
          "MessageVersion": "string",
          "MessageRelease": "string",
          "ApplicationSenderID": "string",
          "ApplicationSenderQualifier": "string",
          "AssociationAssignedCode": "string",
          "TargetNamespace": "string"
        }
      ]
    },
    "IsTestInterchange": true,
    "Id": 0,
    "ProtocolName": "string",
    "SettingsName": "string"
  },
  "BizTalkHostSettings": {
    "EnableStatusReporting": true,
    "LogErrorsToEventLog": true,
    "LogWarningsToEventLog": true,
    "StoreMessagePayload": true
  }
}
```

