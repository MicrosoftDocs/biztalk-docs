---
title: "Get all fallback settings text json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: fd30a8df-9386-42e5-921e-58691ff84f83
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get all fallback settings: text/json
## FallbackSettings

  Response Content Type: **text/json**

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
| Curl | curl -X GET --header 'Accept: text/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/FallbackSettings'|
| Response Body | |
| Response Code | 200|

Response body
---

```
[
  {
    "Id": 1,
    "ProtocolName": "x12",
    "Enabled": true,
    "ReceiverIdentity": {
      "Description": null,
      "Qualifier": "ZZ",
      "Value": "RECEIVE-PARTNER",
      "Id": 2
    },
    "SenderIdentity": {
      "Description": null,
      "Qualifier": "ZZ",
      "Value": "BTS-SENDER",
      "Id": 1
    },
    "X12FallbackProtocolSettings": {
      "ValidationSettings": {
        "ValidateCharacterSet": true,
        "CheckDuplicateInterchangeControlNumber": false,
        "InterchangeControlNumberValidityPeriod": 30,
        "CheckDuplicateGroupControlNumber": false,
        "CheckDuplicateTransactionSetControlNumber": false,
        "ValidateEDITypes": true,
        "ValidateXSDTypes": false,
        "AllowLeadingAndTrailingSpacesAndZeroes": false,
        "TrimLeadingAndTrailingSpacesAndZeroes": false,
        "TrailingSeparatorPolicy": "NotAllowed",
        "ValidationOverrides": []
      },
      "FramingSettings": {
        "DataElementSeparator": 42,
        "ComponentSeparator": 58,
        "ReplaceSeparatorsInPayload": false,
        "ReplaceCharacter": 36,
        "SegmentTerminator": 126,
        "CharacterSet": "UTF8",
        "SegmentTerminatorSuffix": "None"
      },
      "EnvelopeSettings": {
        "ControlStandardsId": 85,
        "UseControlStandardsIdAsRepetitionCharacter": false,
        "SenderApplicationId": "BTS-SENDER",
        "ReceiverApplicationId": "RECEIVE-APP",
        "ControlVersionNumber": "00401",
        "InterchangeControlNumberLowerBound": 1,
        "InterchangeControlNumberUpperBound": 999999999,
        "InterchangeControlNumberRollover": true,
        "EnableDefaultGroupHeaders": false,
        "FunctionalGroupId": null,
        "GroupControlNumberLowerBound": 1,
        "GroupControlNumberUpperBound": 999999999,
        "GroupControlNumberRollover": true,
        "GroupHeaderAgencyCode": "T",
        "GroupHeaderVersion": "00401",
        "TransactionSetControlNumberLowerBound": 1,
        "TransactionSetControlNumberUpperBound": 999999999,
        "TransactionSetControlNumberRollover": true,
        "TransactionSetControlNumberPrefix": null,
        "TransactionSetControlNumberSuffix": null,
        "OverwriteExistingTransactionSetControlNumber": true,
        "GroupHeaderDateFormat": "YYMMDD",
        "GroupHeaderTimeFormat": "HHMM",
        "UsageIndicator": "Test",
        "EnvelopeOverrides": []
      },
      "AcknowledgmentSettings": {
        "NeedTechnicalAcknowledgment": false,
        "BatchTechnicalAcknowledgments": false,
        "NeedFunctionalAcknowledgment": false,
        "FunctionalAcknowledgmentVersion": null,
        "BatchFunctionalAcknowledgments": false,
        "NeedImplementationAcknowledgment": false,
        "ImplementationAcknowledgmentVersion": null,
        "BatchImplementationAcknowledgments": false,
        "NeedLoopForValidMessages": false,
        "SendSynchronousAcknowledgment": true,
        "AcknowledgmentControlNumberPrefix": null,
        "AcknowledgmentControlNumberSuffix": null,
        "AcknowledgmentControlNumberLowerBound": 1,
        "AcknowledgmentControlNumberUpperBound": 999999999,
        "AcknowledgmentControlNumberRollover": true,
        "GeneratePatAK901": false
      },
      "MessageFilter": {
        "MessageFilterType": "Exclude",
        "FilterMessages": []
      },
      "SecuritySettings": {
        "AuthorizationQualifier": "00",
        "AuthorizationValue": null,
        "SecurityQualifier": "00",
        "PasswordValue": null
      },
      "ProcessingSettings": {
        "MaskSecurityInfo": true,
        "ConvertImpliedDecimal": false,
        "PreserveInterchange": false,
        "SuspendInterchangeOnError": false,
        "CreateEmptyXmlTagsForTrailingSeparators": true
      },
      "SchemaSettings": {
        "TargetNamespace": "http://schemas.microsoft.com/BizTalk/EDI/X12/2006",
        "SchemaOverrides": []
      },
      "Id": 1,
      "ProtocolName": "x12",
      "SettingsName": "\"\""
    },
    "EDIFACTFallbackProtocolSettings": null,
    "BizTalkHostSettings": {
      "EnableStatusReporting": false,
      "LogErrorsToEventLog": true,
      "LogWarningsToEventLog": true,
      "StoreMessagePayload": false
    }
  },
  {
    "Id": 2,
    "ProtocolName": "edifact",
    "Enabled": true,
    "ReceiverIdentity": {
      "Description": null,
      "Qualifier": "ZZZ",
      "Value": "RECEIVE-PARTNER",
      "Id": 4
    },
    "SenderIdentity": {
      "Description": null,
      "Qualifier": "ZZZ",
      "Value": "BTS-SENDER",
      "Id": 3
    },
    "X12FallbackProtocolSettings": null,
    "EDIFACTFallbackProtocolSettings": {
      "ValidationSettings": {
        "ValidateCharacterSet": true,
        "CheckDuplicateInterchangeControlNumber": false,
        "InterchangeControlNumberValidityPeriod": 30,
        "CheckDuplicateGroupControlNumber": false,
        "CheckDuplicateTransactionSetControlNumber": false,
        "ValidateEDITypes": true,
        "ValidateXSDTypes": false,
        "AllowLeadingAndTrailingSpacesAndZeroes": false,
        "TrimLeadingAndTrailingSpacesAndZeroes": false,
        "TrailingSeparatorPolicy": "NotAllowed",
        "ValidationOverrides": []
      },
      "FramingSettings": {
        "ServiceCodeListDirectoryVersion": null,
        "CharacterEncoding": null,
        "ProtocolVersion": 1,
        "DataElementSeparator": 43,
        "ComponentSeparator": 58,
        "SegmentTerminator": 39,
        "ReleaseIndicator": 63,
        "RepetitionSeparator": 42,
        "CharacterSet": "UNOB",
        "DecimalPointIndicator": "Comma",
        "SegmentTerminatorSuffix": "None"
      },
      "EnvelopeSettings": {
        "ApplicationReferenceId": null,
        "ApplyDelimiterStringAdvice": false,
        "CommunicationAgreementId": "",
        "CreateGroupingSegments": false,
        "GroupApplicationPassword": null,
        "GroupApplicationReceiverId": null,
        "GroupApplicationReceiverQualifier": null,
        "GroupApplicationSenderId": null,
        "GroupApplicationSenderQualifier": null,
        "GroupAssociationAssignedCode": null,
        "GroupControllingAgencyCode": null,
        "GroupControlNumberPrefix": null,
        "GroupControlNumberSuffix": null,
        "GroupMessageRelease": null,
        "GroupMessageVersion": null,
        "InterchangeControlNumberPrefix": null,
        "InterchangeControlNumberSuffix": null,
        "IsTestInterchange": false,
        "ProcessingPriorityCode": "",
        "ReceiverInternalIdentification": null,
        "ReceiverInternalSubIdentification": null,
        "ReceiverReverseRoutingAddress": null,
        "RecipientReferencePasswordQualifier": null,
        "RecipientReferencePasswordValue": null,
        "SenderInternalIdentification": null,
        "SenderInternalSubIdentification": null,
        "SenderReverseRoutingAddress": null,
        "InterchangeControlNumberLowerBound": 1,
        "InterchangeControlNumberUpperBound": 99999999999999,
        "InterchangeControlNumberRollover": false,
        "EnableDefaultGroupHeaders": false,
        "FunctionalGroupId": null,
        "GroupControlNumberLowerBound": 1,
        "GroupControlNumberUpperBound": 99999999999999,
        "GroupControlNumberRollover": false,
        "TransactionSetControlNumberLowerBound": 1,
        "TransactionSetControlNumberUpperBound": 99999999999999,
        "TransactionSetControlNumberRollover": true,
        "TransactionSetControlNumberPrefix": null,
        "TransactionSetControlNumberSuffix": null,
        "OverwriteExistingTransactionSetControlNumber": true,
        "EnvelopeOverrides": []
      },
      "AcknowledgmentSettings": {
        "NeedTechnicalAcknowledgment": false,
        "BatchTechnicalAcknowledgments": false,
        "NeedFunctionalAcknowledgment": false,
        "BatchFunctionalAcknowledgments": false,
        "NeedLoopForValidMessages": false,
        "SendSynchronousAcknowledgment": true,
        "AcknowledgmentControlNumberPrefix": null,
        "AcknowledgmentControlNumberSuffix": null,
        "AcknowledgmentControlNumberLowerBound": 1,
        "AcknowledgmentControlNumberUpperBound": 99999999999999,
        "AcknowledgmentControlNumberRollover": true
      },
      "MessageFilter": {
        "MessageFilterType": "Exclude",
        "FilterMessages": []
      },
      "ProcessingSettings": {
        "MaskSecurityInfo": true,
        "PreserveInterchange": false,
        "SuspendInterchangeOnError": false,
        "CreateEmptyXmlTagsForTrailingSeparators": true,
        "UseDotAsDecimalSeparator": true
      },
      "SchemaSettings": {
        "TargetNamespace": "http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006",
        "SchemaOverrides": []
      },
      "IsTestInterchange": false,
      "Id": 2,
      "ProtocolName": "edifact",
      "SettingsName": "\"\""
    },
    "BizTalkHostSettings": {
      "EnableStatusReporting": false,
      "LogErrorsToEventLog": true,
      "LogWarningsToEventLog": true,
      "StoreMessagePayload": false
    }
  }
]
```

Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Mon, 24 Apr 2017 07:40:09 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "6850",
  "expires": "-1"
}
```

Example Value
---

```
[
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
]
```