---
description: "Learn more about: Known Issues with AS2 Security"
title: "Known Issues with AS2 Security"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Known Issues with AS2 Security
This topic describes known issues with the security of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] AS2 solutions.

## The AS2 Decoder Will Not Validate that a Certificate Is Configured on the Host or for the Destination Party
 The AS2 decoder will decrypt a message as long as the private certificate for that message is configured in the certificate store. However, the AS2 decoder will not validate that the decryption certificate is the same as the certificate configured on the host. The received message can be encrypted with more than one certificate.

## Storing AS2 Messages in Wire Format Can Lead to a Security Issue
 When certificates are not used, storing AS2 messages in wire format in the non-repudiation receipt (NRR) database is not recommended. Doing so could lead to a security issue.

## Messages or MDNs To Be Stored in the NRR Database Should Be Signed
 To guarantee non-repudiation of receipt, you must establish the authentication and integrity of the applicable message. The recommended way of doing so is by using a digital signature on the message. As a result, if you configure AS2 party properties to store messages or MDNs in the non-repudiation database, you should configure the AS2 properties to sign the messages or MDNs that you are going to store.

## BizTalk Server Will Be Unable to Decrypt a Message Saved in Wire Format If the Certificate Is Not Valid
 **Symptom**

 BizTalk Server is unable to decrypt an inbound AS2 message that was saved in wire format in the non-repudiation database.

 **Possible Cause**

 The certificate required to decrypt the message has expired or been revoked. This is more likely to occur if a certain period of time has elapsed since the AS2 message was saved in the non-repudiation database. If this occurs, you may not have immediate access to a valid certificate for the message.

 **Resolution**

 Acquire a valid certificate for decrypting the message.

## The inner envelope of a signed AS2 message must not be changed after the signature has been calculated
 When an AS2 message is signed, the signature is calculated based on the inner envelope headers and payload. If the inner envelope is changed after the signature is calculated, the signature will be corrupted. The boundary headers, or anything outside the boundary headers, can be changed, but anything within the boundary headers must not be changed.

## Use the same logon for the in-process host instance and the isolated host instance to ensure that Personal store is recognized
 The Personal certificate store will be available for message processing only if the user profile is loaded for the user whose logon credentials are associated with the host instance. The Personal store is used for signing and decryption certificates (the user's own private key). The user profile is loaded by default for the in-process host instance; however, the user profile is not loaded by default for the isolated host instance. You can have an application load the user profile for the isolated host. Alternatively, you can work around this issue by using the same logon for the in-process host instance and the isolated host instance.

 Instead of having an application load the user profile, you can create an empty service to load the profile. For information about creating an empty service, see [How to: Create Windows Services](/dotnet/framework/windows-services/how-to-create-windows-services). After you have created the service, open the Computer Management dialog box, open the Properties dialog box for the service, click the **Log On** tab, select **This Account**, enter the logon name used for the isolated host instance, and then click **OK**. You can then manually start the service to load the user profile for that logon user.

## The Key Usage attribute of a certificate must match the certificate's use
 Certificates used for AS2 transport must have the attributes required for their intended use. For signing and signature verification, the Key Usage attribute of the certificate must be Digital Signature. For encryption and decryption, the Key Usage attribute of the certificate must be Data Encipherment or Key Encipherment. You can verify the Key Usage attribute by double-clicking the certificate, clicking the Details tab in the Certificate dialog box, and checking the Key Usage field.

## The certificate resolution list will be verified for an outgoing MDN if the AS2-To property is not set for the party
 In the default agreement for an outgoing MDN, the certificate resolution list verification is performed. If you do not want this verification to be performed, verify that the correct AS2-To party property is set, so the receiving party can be resolved and the party properties can be determined. If so, the default agreement that prompts verification of the certificate resolution list will not be used. You will also need to disable the Check Certification Revocation List property on the General page of the AS2 party properties.