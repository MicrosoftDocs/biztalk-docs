---
title: "Create an agreement application x-www-form-urlencoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: e807e4d5-2460-4c49-b484-ed928324f69c
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Create an agreement: application/x-www-form-urlencoded
## Create an agreement


  Response Content Type: **application/x-www-form-urlencoded**

Parameters
---



Parameter  |Value  |Descripton  |Parameter Type  |Data Type 
---------|---------|---------|---------|---------
agreement     |(required)|Agreement details.|body|    |

Response Messages
---

HTTP Status Code  |Reason |Response Model|Headers 
---------|---------|---------|---------
204    |No Content    |         |         |



Method  | Request URL
------------- | -------------
GET  | http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Agreements

Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X POST --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: text/plain'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Agreements'|
| Response Body | A partner with name string does not exist.|
| Response Code | 400|


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 04:03:43 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "text/plain; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "42",
  "expires": "-1"
}
```
Example Value
---
Data Type

```
{
  "Id": 0,
  "Name": "string",
  "Description": "string",
  "Protocol": "string",
  "Enabled": true,
  "StartDate": "2017-04-21T00:30:34.762Z",
  "EndDate": "2017-04-21T00:30:34.762Z",
  "SendPartner": {
    "PartnerName": "string",
    "ProfileName": "string",
    "SettingsName": "string"
  },
  "ReceivePartner": {
    "PartnerName": "string",
    "ProfileName": "string",
    "SettingsName": "string"
  },
  "AgreementContent": {
    "AS2AgreementContent": {
      "SendAgreement": {
        "ProtocolSettings": {
          "MessageConnectionSettings": {
            "IgnoreCertificateNameMismatch": true,
            "HttpExpect100ContinueSupported": true,
            "KeepHttpConnectionAlive": true,
            "UnfoldHttpHeaders": true
          },
          "ValidationSettings": {
            "MessageEncrypted": true,
            "MessageSigned": true,
            "MessageCompressed": true,
            "EncryptionAlgorithm": "string",
            "CheckCertificateRevocationListOnSend": true,
            "CheckCertificateRevocationListOnReceive": true,
            "CheckDuplicateMessage": true,
            "InterchangeDuplicatesValidity": 0,
            "OverrideMessageProperties": true
          },
          "ErrorSettings": {
            "SuspendDuplicateMessage": true,
            "ResendIfMDNNotReceived": true,
            "MaxResendAttempts": 0,
            "ResendTimeout": "string",
            "HttpRetryTimeout": "string",
            "OverrideSendPort": true,
            "MinimumHttpRetryInterval": "string",
            "MaximumHttpRetryAttempts": 0,
            "MinimumResendInterval": "string"
          },
          "MDNSettings": {
            "ProcessMDNtoMsgBox": true,
            "NeedMDN": true,
            "SignMDN": true,
            "SendMDNAsynchronously": true,
            "ReceiptDeliveryUrl": "string",
            "DispositionNotificationTo": "string",
            "SignOutboundMDNIfOptional": true,
            "MDNText": "string",
            "MicHashingAlgorithm": "string"
          },
          "EnvelopeSettings": {
            "TransmitFileNameInMimeHeader": true,
            "FileNameTemplate": "string",
            "SuspendMessageOnFileNameGenerationError": true,
            "AutogenerateFileName": true,
            "MessageContentType": "string"
          },
          "SecuritySettings": {
            "OverrideGroupSigningCertificate": true,
            "SigningCertificateName": "string",
            "SigningCertificateThumbprint": "string",
            "EnableNRRForInboundEncodedMessages": true,
            "EnableNRRForInboundDecodedMessages": true,
            "EnableNRRForOutboundMDN": true,
            "EnableNRRForOutboundEncodedMessages": true,
            "EnableNRRForOutboundDecodedMessages": true,
            "EnableNRRForInboundMDN": true
          },
          "AcknowledgmentConnectionSettings": {
            "AckIgnoreCertificateNameMismatch": true,
            "AckHttpExpect100Continue": true,
            "AckKeepHttpConnectionAlive": true,
            "AckUnfoldHttpHeaders": true
          },
          "Id": 0,
          "ProtocolName": "string",
          "SettingsName": "string"
        },
        "Id": 0,
        "SenderBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "ReceiveBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "SendPortNames": [
          "string"
        ],
        "BatchDescriptions": [
          {
            "Id": 0,
            "Name": "string",
            "Description": "string",
            "Protocol": "string",
            "StartDate": "2017-04-21T00:30:34.763Z",
            "EndDate": "2017-04-21T00:30:34.763Z",
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
              "FirstRelease": "2017-04-21T00:30:34.763Z",
              "SendEmptyBatchSignal": true
            }
          }
        ]
      },
      "ReceiveAgreement": {
        "ProtocolSettings": {
          "MessageConnectionSettings": {
            "IgnoreCertificateNameMismatch": true,
            "HttpExpect100ContinueSupported": true,
            "KeepHttpConnectionAlive": true,
            "UnfoldHttpHeaders": true
          },
          "ValidationSettings": {
            "MessageEncrypted": true,
            "MessageSigned": true,
            "MessageCompressed": true,
            "EncryptionAlgorithm": "string",
            "CheckCertificateRevocationListOnSend": true,
            "CheckCertificateRevocationListOnReceive": true,
            "CheckDuplicateMessage": true,
            "InterchangeDuplicatesValidity": 0,
            "OverrideMessageProperties": true
          },
          "ErrorSettings": {
            "SuspendDuplicateMessage": true,
            "ResendIfMDNNotReceived": true,
            "MaxResendAttempts": 0,
            "ResendTimeout": "string",
            "HttpRetryTimeout": "string",
            "OverrideSendPort": true,
            "MinimumHttpRetryInterval": "string",
            "MaximumHttpRetryAttempts": 0,
            "MinimumResendInterval": "string"
          },
          "MDNSettings": {
            "ProcessMDNtoMsgBox": true,
            "NeedMDN": true,
            "SignMDN": true,
            "SendMDNAsynchronously": true,
            "ReceiptDeliveryUrl": "string",
            "DispositionNotificationTo": "string",
            "SignOutboundMDNIfOptional": true,
            "MDNText": "string",
            "MicHashingAlgorithm": "string"
          },
          "EnvelopeSettings": {
            "TransmitFileNameInMimeHeader": true,
            "FileNameTemplate": "string",
            "SuspendMessageOnFileNameGenerationError": true,
            "AutogenerateFileName": true,
            "MessageContentType": "string"
          },
          "SecuritySettings": {
            "OverrideGroupSigningCertificate": true,
            "SigningCertificateName": "string",
            "SigningCertificateThumbprint": "string",
            "EnableNRRForInboundEncodedMessages": true,
            "EnableNRRForInboundDecodedMessages": true,
            "EnableNRRForOutboundMDN": true,
            "EnableNRRForOutboundEncodedMessages": true,
            "EnableNRRForOutboundDecodedMessages": true,
            "EnableNRRForInboundMDN": true
          },
          "AcknowledgmentConnectionSettings": {
            "AckIgnoreCertificateNameMismatch": true,
            "AckHttpExpect100Continue": true,
            "AckKeepHttpConnectionAlive": true,
            "AckUnfoldHttpHeaders": true
          },
          "Id": 0,
          "ProtocolName": "string",
          "SettingsName": "string"
        },
        "Id": 0,
        "SenderBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "ReceiveBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "SendPortNames": [
          "string"
        ],
        "BatchDescriptions": [
          {
            "Id": 0,
            "Name": "string",
            "Description": "string",
            "Protocol": "string",
            "StartDate": "2017-04-21T00:30:34.764Z",
            "EndDate": "2017-04-21T00:30:34.764Z",
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
              "FirstRelease": "2017-04-21T00:30:34.764Z",
              "SendEmptyBatchSignal": true
            }
          }
        ]
      }
    },
    "X12AgreementContent": {
      "SendAgreement": {
        "ProtocolSettings": {
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
        "Id": 0,
        "SenderBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "ReceiveBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "SendPortNames": [
          "string"
        ],
        "BatchDescriptions": [
          {
            "Id": 0,
            "Name": "string",
            "Description": "string",
            "Protocol": "string",
            "StartDate": "2017-04-21T00:30:34.767Z",
            "EndDate": "2017-04-21T00:30:34.767Z",
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
              "FirstRelease": "2017-04-21T00:30:34.767Z",
              "SendEmptyBatchSignal": true
            }
          }
        ]
      },
      "ReceiveAgreement": {
        "ProtocolSettings": {
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
        "Id": 0,
        "SenderBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "ReceiveBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "SendPortNames": [
          "string"
        ],
        "BatchDescriptions": [
          {
            "Id": 0,
            "Name": "string",
            "Description": "string",
            "Protocol": "string",
            "StartDate": "2017-04-21T00:30:34.768Z",
            "EndDate": "2017-04-21T00:30:34.768Z",
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
              "FirstRelease": "2017-04-21T00:30:34.769Z",
              "SendEmptyBatchSignal": true
            }
          }
        ]
      }
    },
    "EDIFACTAgreementContent": {
      "SendAgreement": {
        "ProtocolSettings": {
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
        "Id": 0,
        "SenderBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "ReceiveBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "SendPortNames": [
          "string"
        ],
        "BatchDescriptions": [
          {
            "Id": 0,
            "Name": "string",
            "Description": "string",
            "Protocol": "string",
            "StartDate": "2017-04-21T00:30:34.771Z",
            "EndDate": "2017-04-21T00:30:34.771Z",
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
              "FirstRelease": "2017-04-21T00:30:34.771Z",
              "SendEmptyBatchSignal": true
            }
          }
        ]
      },
      "ReceiveAgreement": {
        "ProtocolSettings": {
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
        "Id": 0,
        "SenderBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "ReceiveBusinessIdentity": {
          "Description": "string",
          "Qualifier": "string",
          "Value": "string",
          "Id": 0
        },
        "SendPortNames": [
          "string"
        ],
        "BatchDescriptions": [
          {
            "Id": 0,
            "Name": "string",
            "Description": "string",
            "Protocol": "string",
            "StartDate": "2017-04-21T00:30:34.773Z",
            "EndDate": "2017-04-21T00:30:34.773Z",
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
              "FirstRelease": "2017-04-21T00:30:34.773Z",
              "SendEmptyBatchSignal": true
            }
          }
        ]
      }
    }
  },
  "CustomSettings": [
    {
      "Name": "string",
      "Value": "string"
    }
  ],
  "Contacts": [
    {
      "Id": 0,
      "Name": "string",
      "Company": "string",
      "JobTitle": "string",
      "Email": "string",
      "WebAddress": "string",
      "BusinessPhone": "string",
      "MobilePhone": "string",
      "Fax": "string",
      "Address": "string",
      "Notes": "string"
    }
  ]
}