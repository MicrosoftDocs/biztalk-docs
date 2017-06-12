---
title: "Update an agreement application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: c686f131-8799-4953-b083-863a6f096622
caps.latest.revision: 2
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Update an agreement: application/json
## Update an agreement

  Response Content Type: **application/json**
  
  Parameters
  ---
  
  

Parameter |Value |Description |Parameter Type|Data Type
---------|---------|---------|---------|---------
agreement |         |Agreement details.|body  |         |
agreementName|(required)    |The current name of the agreement to update. |path     |string |


Response Messages
---

HTTP Status Code|Reason|Response Model|Headers 
---------|---------|---------|---------
204   |No Content    |         |         |

Example Value
---

```
{
  "Id": 0,
  "Name": "string",
  "Description": "string",
  "Protocol": "string",
  "Enabled": true,
  "StartDate": "2017-04-21T00:30:35.146Z",
  "EndDate": "2017-04-21T00:30:35.146Z",
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
            "StartDate": "2017-04-21T00:30:35.146Z",
            "EndDate": "2017-04-21T00:30:35.146Z",
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
              "FirstRelease": "2017-04-21T00:30:35.146Z",
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
            "StartDate": "2017-04-21T00:30:35.146Z",
            "EndDate": "2017-04-21T00:30:35.146Z",
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
              "FirstRelease": "2017-04-21T00:30:35.146Z",
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
            "StartDate": "2017-04-21T00:30:35.149Z",
            "EndDate": "2017-04-21T00:30:35.149Z",
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
              "FirstRelease": "2017-04-21T00:30:35.149Z",
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
            "StartDate": "2017-04-21T00:30:35.149Z",
            "EndDate": "2017-04-21T00:30:35.149Z",
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
              "FirstRelease": "2017-04-21T00:30:35.149Z",
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
            "StartDate": "2017-04-21T00:30:35.151Z",
            "EndDate": "2017-04-21T00:30:35.151Z",
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
              "FirstRelease": "2017-04-21T00:30:35.151Z",
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
            "StartDate": "2017-04-21T00:30:35.152Z",
            "EndDate": "2017-04-21T00:30:35.152Z",
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
              "FirstRelease": "2017-04-21T00:30:35.152Z",
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
```

