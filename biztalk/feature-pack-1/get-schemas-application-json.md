---
title: "Get Schemas application json | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "managed-reference"
ms.assetid: fb117f3d-d218-4d10-9026-93610eaaa557
caps.latest.revision: 3
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Get Schemas: application/json
## Get schemas

  Response Content Type: **application/json**

Request
---
Response Class (Status 200)

OK

Method  | Request URL
------------- | -------------|
GET  |http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Schemas |
Response
---

| Response | Content          |
| ------------- | ----------- |
| Curl | curl -X GET --header 'Accept: application/json' 'http://biztalkfp1.westus.cloudapp.azure.com/BizTalkManagementService/Schemas'|
| Response Code | 200|

## Response Body

```
[
  {
    "Name": "MessageTracking.bts_messagetracking_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/messagetracking-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "MessageTracking.ActivityIdentity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.AdapterTransmitBeginTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.TransmittedFileLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.PortName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.AdapterTransmitCompleteTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.PartyName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.MessageIdentity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.AdapterReceiveCompleteTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.OriginatingMessage",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MessageTracking.AdapterReceiveBeginTime",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "ErrorReport.bts_error_report_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2005/error-report",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "ErrorReport.Description",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.RoutingFailureReportID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.FailureCategory",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.ErrorType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.FailureMessageID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.MessageType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.SendPortName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.ReceivePortName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.FailureAdapter",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.FailureInstanceID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.FailureTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.OutboundTransportLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.ProcessingServer",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.InboundTransportLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "ErrorReport.FailureCode",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "SMTP.bts_smtp_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/smtp-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "SMTP.Username",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.ReadReceipt",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.SMTPAuthenticate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.From",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.DeliveryReceipt",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.SMTPHost",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.EmailBodyTextCharset",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.EmailBodyFileCharset",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.EmailBodyText",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.Subject",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.EmailBodyFile",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.MessagePartsAttachments",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.Attachments",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.CC",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.ReplyBy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SMTP.SMTPTo",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "POP3.bts_pop3_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/pop3-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "POP3.From",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "POP3.To",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "POP3.Subject",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "POP3.ReplyTo",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "POP3.Date",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "POP3.DispositionNotificationTo",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "POP3.Headers",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "POP3.CC",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "WSS.bts_WindowsSharePointServices_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2006/WindowsSharePointServices-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "WSS.Url",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigTimeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InIconUrl",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigSharePointOnlinePassword",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InPropertiesXml",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InItemId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InFileSize",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigTemplatesNamespaceCol",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InEditUrl",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigCustomTemplatesDocLib",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.Filename",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InListName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InTitle",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InCreated",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InArchivedMsgUrl",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InCreatedBy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigOfficeIntegration",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InListUrl",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigUseClientOM",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InOfficeIntegration",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InLastModified",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigPropertiesXml",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigCustomTemplatesNamespaceCol",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigSharePointOnlineUsername",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigNamespaceAliases",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.InLastModifiedBy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigOverwrite",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigTemplatesDocLib",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WSS.ConfigAdapterWSPort",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "LEGACY.bts_legacy_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/legacy-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "LEGACY.SubmissionHandle",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.DestinationQualifier",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.DestinationID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.EnvelopeName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.FilePath",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.Openness",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.ChannelName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.SourceQualifier",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.PassThru",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.DocSpecName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "LEGACY.SourceID",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "MIME.bts_mime_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/mime-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "MIME.PartContentTypeSecondaryHeaderValue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.ContentTypeSecondaryHeader",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.IsMultipartRelated",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.IsMIMEEncoded",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.FileName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.ContentTransferEncoding",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.PartContentTypeSecondaryHeader",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.ContentTypeSecondaryHeaderValue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.ContentDescription",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.ContentLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.PassThroughBTF",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MIME.ContentID",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "MSMQT.MSMQT_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/msmqt-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "MSMQT.InboundCorrelationId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.EncryptionAlgorithm",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.PrivLevel",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.ResponseQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.SenderID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Priority",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.InboundResponseQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.LastFragment",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.AuthLevel",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.IsLastInTransaction",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.FragmentN",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.RouterName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.SeqN",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.OrderQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.NonTransactionalQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.SenderIDType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.TransactionId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.AdminQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Version",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.DestinationQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Trace",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.CorrelationId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.WakeupTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.SenderIDLength",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Authenticated",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.MsgID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Class",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Delivery",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Acknowledge",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Signature",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.SourceMachineGuid",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Audit",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.SentTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.SeqID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.HashAlg",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.IsSecurityIncluded",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.IsXactMsg",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.TimeToReachQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.TimerChain",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.IsAuthenticated",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Extension",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.AppSpecific",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.ArrivedTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.SignatureSize",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.IsFirstInTransaction",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.OutboundTransportLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.Label",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.PrevN",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQT.MessageType",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "Microsoft.BizTalk.XLANGs.BTXEngine.XLANGsBizTalkProperties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/xlangs-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "Microsoft.BizTalk.XLANGs.BTXEngine.SendingOrchestrationType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorPID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "Microsoft.BizTalk.XLANGs.BTXEngine.SendingOrchestrationID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "Microsoft.BizTalk.XLANGs.BTXEngine.BodyPartIndex",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "SOAP.bts_soap_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/soap-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "SOAP.ProxyUsername",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.UnknownHeaders",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.UseSoap12",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.AuthenticationScheme",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.UseHandlerSetting",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.UseSSO",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.ClientConnectionTimeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.Username",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.AffiliateApplicationName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.UseProxy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.MethodName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.AssemblyName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.ClientCertificate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.ProxyAddress",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.ProxyPort",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.TypeName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SOAP.UserDefined",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "BTS.bts_system_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/system-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "BTS.InboundTransportLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SuppressRoutingFailureDiagnosticInfo",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckDescription",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.WorkID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ReceivePipelineConfig",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SOAPAction",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.OutboundTransportCLSID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.DestinationParty",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.InterchangeSequenceNumber",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SourcePartyEvidence",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.JobID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckInboundTransportLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SuspendMessageOnRoutingFailure",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.DestinationPartyQualifier",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SPTransportBackupID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ReceivePortTransformHint",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.OutboundTransportType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.OutboundTransportLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.TransmitWorkID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.PropertiesToUpdate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SuspendMessageOnMappingFailure",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckOutboundTransportLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.MessageID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SourceParty",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.DestinationPartyID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ReceivePortID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SuspendAsNonResumable",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ExpirationTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.RetryInterval",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.MessageDestination",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.WindowsUser",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.FaultQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ReqRespTransmitPipelineID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckFailureCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.FaultName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SPGroupID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SendPortTransformHint",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.BatchRequired",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.InterchangeID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SourcePartyQualifier",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.PipelinesExecuted",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ReceivePipelineResponseConfig",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.IsRequestResponse",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckOwnerID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SPTransportID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.BackupEndpointInfo",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SPID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckReceivePortID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SigningCert",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SourcePartyID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.EpmRRCorrelationToken",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckFailureCategory",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.InboundTransportType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.PartnerPort",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.BizTalkControl",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.DecryptionCert",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.IsSolicitResponse",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.LTPMsgBodyTracking",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckSendPortName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckSendPortID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.RouteDirectToTP",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SendPipelineConfig",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.PartnerService",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.EncryptionCert",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SchemaStrongName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.CorrelationToken",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckRequired",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.IsFragmented",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ActionOnFailure",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SSOTicket",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.MessageExchangePattern",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ReceivePipelineID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckReceivePortName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ProcessingParts",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.LastInterchangeMessage",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.TransmitPipelineID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SourcePartyEvidenceQualifier",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.IsDynamicSend",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.EndpointGroup",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ActivationServiceID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AckID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.MessageType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SignatureCertificate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.RetryCount",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SPName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.SendPipelineResponseConfig",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.ReceivePortName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.PassThrough",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.LRPMsgBodyTracking",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.LoopBack",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.Operation",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "XMLNORM.bts_xmlnorm_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/xmlnorm-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "XMLNORM.PreserveBom",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.ProcessingInstruction",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.DocumentSpecName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.InboundPropertiesTracked",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.BamTrackingOnly",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.RecoverableInterchangeProcessing",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.PromotePropertiesOnly",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.HeaderSpecName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.AllowUnrecognizedMessage",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.TrailerSpecName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.ProcessingInstructionOption",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.TargetCharset",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.EnvelopeSpecName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.AddXMLDeclaration",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.FlatFileHeaderDocument",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.ProcessingInstructionScope",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "XMLNORM.SourceCharset",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "HTTP.bts_http_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/http-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "HTTP.Certificate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.ProxyName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.ProxyPort",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.UserHttpHeaders",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.SubmissionHandle",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.HttpCookie",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.RequestTimeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.AuthenticationScheme",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.UseProxy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.UseSSO",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.EnableChunkedEncoding",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.ContentType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.ProxyUsername",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.MaxRedirects",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.Username",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.InboundHttpHeaders",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.AffiliateApplicationName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.ResponseStatusCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "HTTP.UseHandlerProxySettings",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "SQL.bts_SQL_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/sql-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "SQL.DocumentTargetNamespace",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SQL.ResponseDocumentRootElementName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SQL.ConnectionString",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "WCF.WCFPropertySchema",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "WCF.ServiceCertificate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.InboundBodyLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.IssuerName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.IssuerSecret",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MsmqProtectionLevel",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.UseSSO",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.IsFault",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.CloseTimeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.SecurityMode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.IsolationLevel",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.OrderedProcessing",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.InboundHttpHeaders",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MaxReceivedMessageSize",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.NegotiateServiceCredential",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MsmqSecureHashAlgorithm",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.ClientCertificate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.SessionIdleTimeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.OpenTimeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.ReplyToAddress",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.EstablishSecurityContext",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MessageClientCredentialType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MaxConnections",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.EndpointBehaviorConfiguration",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.FromAddress",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.SuppressMessageBodyForHttpVerbs",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.HttpHeaders",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.StsUri",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.VariablePropertyMapping",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.InboundHttpMethod",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.InboundNodeEncoding",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.HttpMethodAndUrl",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.InboundBodyPathExpression",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MsmqAuthenticationMode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.TransportClientCredentialType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.UseSasAuthentication",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.DeadLetterQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.Headers",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.UseAcsAuthentication",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.UseSourceJournal",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.Password",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.SuspendMessageOnFailure",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.InboundHttpStatusCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.ProxyToUse",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.TransportProtectionLevel",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.SharedAccessKeyName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.TransactionProtocol",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MessageEncoding",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.InboundHttpStatusDescription",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.OutboundXmlTemplate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.AffiliateApplicationName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.UserName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.OutboundCustomHeaders",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.EnableTransaction",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.DisableLocationOnFailure",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MsmqEncryptionAlgorithm",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.BindingConfiguration",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.ServiceBehaviorConfiguration",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.TextEncoding",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.SendTimeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.Action",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.LeaseTimeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.PropagateFaultMessage",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.OutboundBodyLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.To",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.CustomDeadLetterQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.ProxyUserName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.InboundHeaders",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.BindingType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.SharedAccessKey",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.MaxConcurrentCalls",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.ReferencedBindings",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.TimeToLive",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.OutboundHttpStatusCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.ProxyPassword",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.AlgorithmSuite",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.ProxyAddress",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.Identity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "WCF.OutboundHttpStatusDescription",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "SBMessaging.SBMessagingBrokeredMessagePropertySchema",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2012/Adapter/BrokeredMessage-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "SBMessaging.EnqueuedTimeUtc",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.ReplyToSessionId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.LockToken",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.TimeToLive",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.MessageId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.ContentType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.CustomBrokeredMessagePropertyNamespace",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.LockedUntilUtc",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.ExpiresAtUtc",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.ReplyTo",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.CorrelationId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.Label",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.To",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.ScheduledEnqueueTimeUtc",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.SessionId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.SequenceNumber",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SBMessaging.DeliveryCount",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "MLLP.bts_mllp_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BTAHL7/2004/Messaging/Transports/mllp-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "MLLP.noSB",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.startBlockDelimiter",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.suspendOnMLLPTransNAK",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.timeout",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.connectionName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.solicitResponseEnabled",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.comments",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.carriageReturn",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.persistentConnection",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.useMLLPTransAck",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.endBlockDelimiter",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.ackSubmitReceiveLocation",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MLLP.acceptableACKCodes",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "SFTP.bts_sftp_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2012/Adapter/sftp-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "SFTP.PrivateKeyPassword",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.ProxyPassword",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.ProxyPort",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.AppendIfExists",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.ProxyType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.ProxyUserName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.AccessAnyServerHostKey",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.PrivateKeyFile",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.ProxyAddress",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.ReceivedFileName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.Log",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.TargetFileName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.UserName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.EncryptionCipher",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.Password",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.SSHServerHostKeyFingerPrint",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.ClientAuthenticationMode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "SFTP.TemporaryFolder",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "BTS.bts_endpoint_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/endpoint-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "BTS.TwoWayReceivePort",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "FILE.bts_file_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/file-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "FILE.Username",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FILE.AllowCacheOnWrite",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FILE.CopyMode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FILE.ReceivedFileName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FILE.TargetFileName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FILE.FileCreationTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FILE.UseTempFileOnWrite",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "FTP.bts_ftp_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/ftp-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "FTP.AfterPut",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.UserName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.CommandLogFileName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.MaxConnections",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.FtpServerType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.PassiveMode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.SpoolingFolder",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.ReceivedFileName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.UseDataProtection",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.SSOAffiliateApplication",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.BeforePut",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.RepresentationType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.AppendIfExists",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.FtpsConnectionMode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.UseSsl",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.ClientCertificateHash",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "FTP.AllocateStorage",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "BTS.bts_appstream_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/system-properties/appstream",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "BTS.AppStreamEnd",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AppStreamGUID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AppStreamN",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.AppStreamPrev",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.InAppStreamPrev",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.InAppStreamGUID",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.InAppStreamN",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTS.InAppStreamEnd",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "BTF2.bts_btf2_properties",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/btf2-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "BTF2.prc_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.commitmentRct_commitmentCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.deliveryRct_identity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.fault_faultcode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.commitmentRct_decision",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.commitmentRct_identity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.svc_deliveryRctRqt_sendTo_address",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.commitmentRct_decidedAt",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.svc_commitmentRctRqt_sendTo_address",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.IsReliable",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.prc_instance",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.prop_topic",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.eps_to_address_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.eps_from_address",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.prop_sentAt",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.svc_deliveryRctRqt_sendBy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.fault_faultstring",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.prop_identity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.PassAckThrough",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.svc_commitmentRctRqt_sendTo_address_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.svc_deliveryRctRqt_sendTo_address_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.eps_to_address",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.deliveryRct_receivedAt",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.eps_from_address_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.svc_commitmentRctRqt_sendBy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2.fault_faultactor",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "BTS.soap_envelope_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-envelope",
    "RootName": "Body",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-envelope",
    "RootName": "Envelope",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-envelope",
    "RootName": "Fault",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-envelope",
    "RootName": "Header",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-envelope",
    "RootName": "NotUnderstood",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-envelope",
    "RootName": "Upgrade",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.xml",
    "TargetNameSpace": "http://www.w3.org/XML/1998/namespace",
    "RootName": "typeOnlySchema",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "WCF.WebHttp.EmptyMessage.WCF_WebHttp_EmptyMessageSchema",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2014/01/Adapters/WCF-WebHttp.EmptyMessage",
    "RootName": "WCF-WebHttpMessageBody",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "anyType",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "anyURI",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "base64Binary",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "boolean",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "byte",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "date",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "dateTime",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "decimal",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "double",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "duration",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "ENTITIES",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "ENTITY",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "float",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "gDay",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "gMonth",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "gMonthDay",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "gYear",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "gYearMonth",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "hexBinary",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "ID",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "IDREF",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "IDREFS",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "int",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "integer",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "language",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "long",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "Name",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "NCName",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "negativeInteger",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "NMTOKEN",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "NMTOKENS",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "nonNegativeInteger",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "nonPositiveInteger",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "normalizedString",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "positiveInteger",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "QName",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "short",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "string",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "time",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "token",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "unsignedByte",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "unsignedInt",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "unsignedLong",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__2",
    "TargetNameSpace": "http://www.w3.org/2003/05/soap-encoding",
    "RootName": "unsignedShort",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTF2Schemas.btf2_process_header",
    "TargetNameSpace": "http://schemas.biztalk.org/btf-2-0/process",
    "RootName": "process",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTF2Schemas.btf2_properties_header",
    "TargetNameSpace": "http://schemas.biztalk.org/btf-2-0/properties",
    "RootName": "properties",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTF2Schemas.btf2_envelope",
    "TargetNameSpace": "http://schemas.biztalk.org/btf-2-0/envelope",
    "RootName": "Envelope",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.deliveryRct_receivedAt",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.eps_from_address_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.deliveryRct_identity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.prop_identity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.svc_commitmentRctRqt_sendTo_address_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.commitmentRct_commitmentCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.prop_sentAt",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.eps_to_address",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.commitmentRct_decidedAt",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.eps_to_address_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.commitmentRct_identity",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.prop_topic",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.commitmentRct_decision",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.svc_deliveryRctRqt_sendTo_address",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.ExpirationTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.prc_type",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.svc_commitmentRctRqt_sendBy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.svc_deliveryRctRqt_sendBy",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.prc_instance",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.svc_commitmentRctRqt_sendTo_address",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.eps_from_address",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "BTF2Schemas.btf2_envelope.svc_deliveryRctRqt_sendTo_address_type",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "BTF2Schemas.btf2_manifest_header",
    "TargetNameSpace": "http://schemas.biztalk.org/btf-2-0/manifest",
    "RootName": "manifest",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTF2Schemas.btf2_receipt_header",
    "TargetNameSpace": "http://schemas.biztalk.org/btf-2-0/receipts",
    "RootName": "commitmentReceipt",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTF2Schemas.btf2_receipt_header",
    "TargetNameSpace": "http://schemas.biztalk.org/btf-2-0/receipts",
    "RootName": "deliveryReceipt",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "anyType",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "anyURI",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "Array",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "base64Binary",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "boolean",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "byte",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "date",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "dateTime",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "decimal",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "double",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "duration",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "ENTITIES",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "ENTITY",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "float",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "gDay",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "gMonth",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "gMonthDay",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "gYear",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "gYearMonth",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "hexBinary",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "ID",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "IDREF",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "IDREFS",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "int",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "integer",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "language",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "long",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "Name",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "NCName",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "negativeInteger",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "NMTOKEN",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "NMTOKENS",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "nonNegativeInteger",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "nonPositiveInteger",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "normalizedString",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "NOTATION",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "positiveInteger",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "QName",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "short",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "string",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "Struct",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "time",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "token",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "unsignedByte",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "unsignedInt",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "unsignedLong",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_encoding_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/encoding/",
    "RootName": "unsignedShort",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/envelope/",
    "RootName": "Body",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/envelope/",
    "RootName": "Envelope",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/envelope/",
    "RootName": "Fault",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTS.soap_envelope_1__1",
    "TargetNameSpace": "http://schemas.xmlsoap.org/soap/envelope/",
    "RootName": "Header",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTF2Schemas.btf2_services_header",
    "TargetNameSpace": "http://schemas.biztalk.org/btf-2-0/services",
    "RootName": "services",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "BTF2Schemas.btf2_endpoints_header",
    "TargetNameSpace": "http://schemas.biztalk.org/btf-2-0/endpoints",
    "RootName": "endpoints",
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Document",
    "Description": null,
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "MSMQ.MSMQPropertySchema",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/msmq-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "MSMQ.Label",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.SourceMachine",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.CorrelationId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.MaximumMessageSize",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.TimeOutUnits",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.UseDeadLetterQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.Acknowledgement",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.SentTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.MessageType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.SegmentationSupport",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.Recoverable",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.UseJournalQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.ArrivedTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.AdministrationQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.UseAuthentication",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.AcknowledgeType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.EncryptionAlgorithm",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.Authenticated",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.CertificateThumbPrint",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.ResponseQueue",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.Priority",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.Transactional",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.AppSpecific",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.BodyType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.TimeOut",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MSMQ.Id",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "MQSeries.MQSPropertySchema",
    "TargetNameSpace": "http://schemas.microsoft.com/BizTalk/2003/mqs-properties",
    "RootName": null,
    "ApplicationName": "BizTalk.System",
    "AssemblyName": "MQSeries, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35",
    "SchemaType": "Property",
    "Description": null,
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_Persistence",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_ErrorOffset",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_Function",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_CancelCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_CodedCharSetId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_ReplyToQMgr",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_UserIdentifier",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_MsgFlags",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_PutApplName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_ReplyToQMgr",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_Format",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_Authenticator",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_Flags",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_UOWControl",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_OriginalLength",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_BackoutCount",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_Report",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_Format",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_PutApplName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_ADSDescriptor",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_Format",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_Flags",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_Persistence",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_AbendCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_PutTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_CommitMode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_MsgId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_TranState",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_ApplIdentityData",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_Feedback",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_MFSMapName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_Reason",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_MsgType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_MsgSeqNumber",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_FacilityLike",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_PutApplType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_ReplyToQ",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_ReturnCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_PutTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_LinkType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_OutputDataLength",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.DynamicReceive",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.Ordered",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_ApplOriginData",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_ReplyToFormat",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.SegmentationAllowed",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_TransactionId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_ApplOriginData",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_RemoteQName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_CorrelId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_MsgType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_TranInstanceId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_ReplyToQ",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_ConversationalTask",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_Expiry",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_MsgId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.SSOAffiliateApplication",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_AccountingToken",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_GroupId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_PutDate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_Facility",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_CodedCharSetId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_Report",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_FacilityKeepTime",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_GetWaitInterval",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_Priority",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_ReplyToFormat",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_SecurityScope",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_AttentionId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQIIH_LTermOverride",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_Encoding",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_Offset",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_AccountingToken",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_PutDate",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_NextTransactionId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.DataConversion",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_ApplIdentityData",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_CompCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_CursorPosition",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_StartCode",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_Authenticator",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_Encoding",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.WaitInterval",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_PutApplType",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_Expiry",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_Format",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.TransactionSupported",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQCIH_TaskEndStatus",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_RemoteQMgrName",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_BackoutCount",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_CorrelId",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQMD_Feedback",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.CompleteMessage",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_Priority",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.MQXQH_MsgDesc_UserIdentifier",
          "TrackingEnabled": false
        },
        {
          "PropertyName": "MQSeries.BizTalk_CorrelationID",
          "TrackingEnabled": false
        }
      ]
    }
  },
  {
    "Name": "AddDataToSQL.Orders",
    "TargetNameSpace": "http://AddDataToSQL.Orders",
    "RootName": "Order",
    "ApplicationName": "OldOrdersReceive",
    "AssemblyName": "OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0",
    "SchemaType": "Document",
    "Description": "",
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "AddDataToSQL.OrderEnvelope",
    "TargetNameSpace": "http://AddDataToSQL.OrderEnvelope",
    "RootName": "OrderEnvelope",
    "ApplicationName": "OldOrdersReceive",
    "AssemblyName": "OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0",
    "SchemaType": "Document",
    "Description": "",
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "AddDataToSQL.TypedProcedure_dbo",
    "TargetNameSpace": "http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo",
    "RootName": "addOldOrders",
    "ApplicationName": "OldOrdersReceive",
    "AssemblyName": "OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0",
    "SchemaType": "Document",
    "Description": "",
    "Tracking": {
      "TrackedProperties": []
    }
  },
  {
    "Name": "AddDataToSQL.TypedProcedure_dbo",
    "TargetNameSpace": "http://schemas.microsoft.com/Sql/2008/05/TypedProcedures/dbo",
    "RootName": "addOldOrdersResponse",
    "ApplicationName": "OldOrdersReceive",
    "AssemblyName": "OldOrdersReceive, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2aa35c52bb10d3e0",
    "SchemaType": "Document",
    "Description": "",
    "Tracking": {
      "TrackedProperties": []
    }
  }
]
```


Response Headers
---

```
{
  "pragma": "no-cache",
  "date": "Fri, 21 Apr 2017 05:27:42 GMT",
  "server": "Microsoft-IIS/10.0",
  "x-aspnet-version": "4.0.30319",
  "x-powered-by": "ASP.NET",
  "content-type": "application/json; charset=utf-8",
  "cache-control": "no-cache",
  "content-length": "92587",
  "expires": "-1"
}
```

Example Value
---

```
[
  {
    "Name": "string",
    "TargetNameSpace": "string",
    "RootName": "string",
    "ApplicationName": "string",
    "AssemblyName": "string",
    "SchemaType": "string",
    "Description": "string",
    "Tracking": {
      "TrackedProperties": [
        {
          "PropertyName": "string",
          "TrackingEnabled": true
        }
      ]
    }
  }
]

```
