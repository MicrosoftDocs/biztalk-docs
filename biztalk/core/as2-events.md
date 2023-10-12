---
description: "Learn more about: AS2 Events"
title: "AS2 Events"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# AS2 Events
The following table lists event messages that may be posted in the event log during AS2 processing.  
  
> [!NOTE]
>  For more information about the AS2 errors listed in the following table, see [EDI and AS2 Events](../core/edi-and-as2-events.md).  
  
|Error Code|Condition|  
|----------------|---------------|  
|AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError|The AS2 Decoder was unable to locate the Disposition-Notification-Options HTTP header which is required for MDN generation.|  
|SynchronousMdnRequestedOnOneWayReceivePortError|Configuration error.  Synchronous MDN requested on a one way HTTP receive Port.|  
|SynchronousMdnRequestedOnOneWaySendPortError|Configuration error.  Synchronous MDN requested on one way HTTP send port.|  
|EncryptionCertNotConfiguredError|The Encryption Certificate has not been configured for AS2 party.  AS2-From: {0} AS2-To: {1}|  
|AS2DecoderPartySigningConfigurationError|Configuration error.  The message signing doesn't match the expected value.  Contact the sending partner and verify signature use.  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"|  
|AS2DecoderExceptionEncounteredDuringProcessing|The AS2 Decoder encountered an exception during processing.  Details of the message and exception are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" MessageType: "{3}" Exception:"{4}"|  
|AS2DecoderMdnMicFailureDuringProcessing|The AS2 Decoder failed processing when validating the MIC value returned in the MDN.  Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"|  
|AS2DecoderMdnSigningMismatchFailureDuringProcessing|The AS2 Decoder failure processing because the MDN signing did not match our request.  Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"|  
|AS2DecoderMdnProcessingFailureReturned|The AS2 Decoder failure processing because the MDN indicated the AS2 message failed processing.  Details of the MDN message are as follows:  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}" OriginalMessageID:"{3}"|  
|AS2InvalidQuotedStringHeaderError|An invalid quoted HTTP header encountered.  Details are as follows:  Header Name: "{0}"  Header Value: "{1}"|  
|AS2MicDataStoreDuplicateMicError|Error Mic entry already exists.|  
|AS2StreamingNonSeekableStreamError|This is a non-seekable stream.|  
|AS2StreamingSetLengthError|The length of this stream cannot be set.|  
|AS2StreamingWriteToReadonlyStreamError|This is a read-only stream.|  
|AS2StreamingMethodNotImplementedError|The method or operation is not implemented.|  
|BtsMimeExceptionEncounteredDuringMessageDecoding|A BTS MIME error was encountered when attempting to decode an AS2 message.  AS2-From: {0}, AS2-To: {1}, MessageId: {2}, Error: {3}|  
|AS2DecoderPartyEncryptionConfigurationError|Configuration error.  The message encryption doesn't match the expected value.  Contact the sending partner and verify encryption use.  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"|  
|AS2DecoderPartySignatureError|Configuration error.  The message signature doesn't match the signature configured for this party.  Contact the sending partner and verify the certificate used.  AS2-From:"{0}" AS2-To:"{1}" MessageID:"{2}"|  
|InvalidAgreementAS2FromName|The party for this AS2 interchange must contain a value for AS2-From.|  
|InvalidAgreementAS2ToName|The party for this AS2 interchange must contain a value for AS2-To.|  
|UnsupportedAS2HashAlgorithmError|The hash algorithm specified in the AS2 message is unsupported.|  
|UnableToLocateAS2PartyError|Unable to access party using qualifier: {0} party: {1}.  Error: {2}|  
|UnableToLocateAS2PartyByPartyNameError|Unable to access party using party: {0}.|  
|UnableToLocateAS2PartyBySendPortNameError|Unable to access party using send port: {0}  Error: {1}.|  
|InvalidAS2FromNameConfiguredError|Invalid AS2-From name configured for Party: {0}   Value: {1}|  
|InvalidAS2ToNameConfiguredError|Invalid AS2-To name configured for Party: {0}   Value: {1}|  
|InvalidAS2FromNameHeaderReceivedError|Invalid AS2-From header received.  Value: {0}|  
|InvalidAS2ToNameHeaderReceivedError|Invalid AS2-To header received.  Value: {0}|  
|MissingAS2FromHeaderError|An AS2 message was received that did not contain the AS2-From header.|  
|MissingAS2ToHeaderError|An AS2 message was received that did not contain the AS2-To header.|  
|InvalidDispositionNotificationOptionToError|Disposition-Notification-Option value: "{0}" is invalid.  {1}|  
|InvalidReceiptDeliveryOptionError|Receipt-Delivery-Option value: "{0}" is invalid.  {1}|  
|InvalidOrMissingASN1DataLengthHeader|Invalid or missing ASN.1 Data Length field encountered during decompression processing.|  
|InvalidOrMissingASN1TrailingBytes|Invalid or missing trailing ASN.1 CMS compressed structure bytes during decompression processing.|  
|InvalidASN1CompressedStructureEncountered|Invalid ASN.1 compressed structure encountered during decompression processing.|  
|InvalidOrMissingDataHeaderEncountered|Invalid or missing ASN.1 compressed header encountered during decompression processing.|  
|InvalidOptionalZLibFieldEncountered|Invalid ASN.1 ZLib compression field encountered during decompression processing.|  
|InvalidOrMissingDataOIDEncountered|Invalid or missing ASN.1 Data OID encountered during decompression processing.|  
|InvalidOrMissingZLibOIDEncountered|Invalid or missing ASN.1 ZLib OID encountered during decompression processing.|  
|InvalidOrMissingCompressedDataOIDEncountered|Invalid or missing ASN.1 Compressed Data OID encountered during decompression processing.|  
|InvalidAdler32ChecksumInCompressedMessageError|Invalid Adler32 checksum encountered.|  
|UnsupportedOctetStringLengthEncountered|Unsupported Octet string length encountered.  Maximum supported octet length is 4.|  
|DecompressionFailedError|Decompression failed while processing a compressed AS2 message.  Error: {0}|  
|DecryptionFailedError|An error occurred when decrypting an AS2 message.|  
|IntegrityCheckFailedError|An error occurred when validating an AS2 message.  Make sure the certificates used have not timed out or been revoked.|  
|EncryptionCertificateHasBeenRevokedError|The certificate used to encrypt a message has been revoked. Certificate thumbprint: {0}|  
|DecryptionCertificateHasBeenRevokedError|The certificate used to decrypt a message has been revoked. Certificate thumbprint: {0}|  
|SigningCertificateHasBeenRevokedError|The certificate used for signing a message has been revoked. Certificate thumbprint: {0}|  
|SignatureCertificateHasBeenRevokedError|The certificate used for signing a message has been revoked. Certificate thumbprint: {0}|  
|CertificateMissingError|The certificate used for signing a message cannot be located in the local certificate store. Certificate thumbprint: {0}|  
|EmptyContentOnAS2MessageEncountered|An empty AS2 message was received.  The message will be suspended.|  
|AS2FromMatchesAS2ToError|The AS2-From value matches the AS2-To value.|  
|GenericEdiIntException|An EdiInt exception has occurred.|  
|BtsMimeExceptionEncounteredDuringMessageEncoding|A BTS MIME error was encountered when attempting to encode a message.  Error: {0}, HResult:{1}|  
|BtsMimeGeneralExceptionEncounteredDuringMessageEncoding|A BTS MIME error was encountered when attempting to encode a message.  Error: {0}|  
|AS2StatusReportingExceptionEncountered|An error was encountered when attempting to generate an AS2 status report.  Error: {0}|
