---
title: "Known Issues with Certificates in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab58264b-2475-4831-9f08-bfbaa293022f
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with Certificates in BizTalk Server
This section describes known issues with managing digital certificates used with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## General Certificate Issues  
  
### Lack of connectivity to the certificate revocation list will cause a certificate to be rejected  
 This issue involves the following error: “There was an authentication error. The status of the certification authority (CA) that issued the certificate used to sign the message is unknown." This error can occur even when the signing certificate is valid when viewed under MMC (using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] user) on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 This condition can occur if the "Check Certificate Revocation" property is enabled on the S/MIME decoder component in the receive pipeline. When this property is set to true, BizTalk Server will try to query the Certificate Revocation List (CRL) to see if the incoming certificate has been revoked. It does not matter if the certificate itself is not revoked. If BizTalk Server cannot query the corresponding CRL because of connectivity issues, it will not accept the certificate. To troubleshoot this error, display the certificate's properties by double-clicking the certificate that you used. In its Details tab, you will see the attribute "CRL Distribution Point" in the field list. There should be several URLs in this attribute that point to the CRL on your CA server. The BizTalk server must be able to access any of these URLs to retrieve the CRL. Otherwise, the revocation checking will fail and the above error will be posted.  
  
### The Other People Certificate store is not initialized until accessed  
 This issue involves the following certificate store error when you try to add or modify send/receive ports/locations using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator console remotely: “Could not open certificate store.” and “The system cannot find the file specified. (System)”.  
  
> [!NOTE]
>  You can modify these artifacts using the administration console if you log on directly to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 On a newly installed computer, the **Other People Certificate** store is not initialized unless you access it once. During the group configuration, you can initialize this **Other People Certificate** store, and as a result not see this error on a computer on which group configuration has been done.  
  
### BizTalk Server only supports one personal certificate for each BizTalk group  
 The personal certificate that is used by the BizTalk group is specified by setting the thumbprint of the personal certificate in the BizTalk group properties. A BizTalk group can represent an enterprise, a department, a hub, or another business unit.  
  
## AS2 Certificate Issues  
  
### The AS2 decoder will not validate that a certificate is configured on the host or for the destination party  
 The AS2 decoder will decrypt a message as long as the private certificate for that message is configured in the certificate store. However, the AS2 decoder will not validate that the decryption certificate is the same as the certificate configured on the host. The received message can be encrypted with more than one certificate.  
  
### BizTalk Server will be unable to decrypt a message saved in wire format if the certificate is not valid  
 **Symptom**  
  
 BizTalk Server is unable to decrypt an inbound AS2 message that was saved in wire format in the non-repudiation database.  
  
 **Possible Cause**  
  
 The certificate required to decrypt the message has expired or been revoked. This is more likely to occur if a certain period of time has elapsed since the AS2 message was saved in the non-repudiation database. If this occurs, you may not have immediate access to a valid certificate for the message.  
  
 **Resolution**  
  
 Acquire a valid certificate for decrypting the message.  
  
### If an AS2 message cannot be decrypted, the problem may be fixed by re-importing the certificate  
 **Symptom**  
  
 The AS2 Decoder encounters an exception when it attempts to decrypt an AS2 message, throwing the following error:  
  
```  
"The AS2 Decoder encountered an exception during processing. Details of the message and exception are as follows:   
   AS2-From:"PARTNER" AS2-To:"HOME" MessageID:"<137706.1178060412333@servername>"   
   MessageType: "unknown" Exception:"An error occurred when decrypting an AS2 message."  
System.ArgumentNullException: Value cannot be null.  
Parameter name: PayloadContentType  
at Microsoft.BizTalk.Edi.Reporting.Common.Utilities.ValidateArgument(Object o,  
String parameterName, Boolean isEmptyStringValidationRequired)  
at Microsoft.BizTalk.EdiInt.Reporting.AS2MessageActivity.ValidateParameters()  
at Microsoft.BizTalk.EdiInt.Reporting.AS2MessageActivity.Create()"  
  
```  
  
 **Possible Cause**  
  
 The certificate used to decrypt the AS2 message needs to be reloaded into the Personal Store.  
  
 **Resolution**  
  
 Delete the existing certificate from the Personal Store, and then re-import the certificate into the Personal Store using the Certificate Import Wizard. Do so by right-clicking the **Certificate** folder under the **Personal Store**, pointing to **All Tasks**, and then clicking **Import**.  
  
### Use the same logon for the in-process host instance and the isolated host instance to ensure that personal store is recognized  
 The Personal certificate store will be available for message processing only if the user profile is loaded for the user whose logon credentials are associated with the host instance. The Personal store is used for signing and decryption certificates (the user's own private key). The user profile is loaded by default for the in-process host instance; however, the user profile is not loaded by default for the isolated host instance. You can have an application load the user profile for the isolated host. Alternatively, you can work around this issue by using the same logon for the in-process host instance and the isolated host instance.  
  
 Instead of having an application load the user profile, you can create an empty service to load the profile. For more information about creating an empty service, see [How to: Create Windows Services](http://go.microsoft.com/fwlink/?LinkId=155149) (http://go.microsoft.com/fwlink/?LinkId=155149) in Visual Studio Help.  
  
 After creating the empty service to load the profile, proceed as follows:  
  
1.  Click **Start**, and then click **Run** to open the **Run** dialog box.  
  
2.  In the **Run** dialog box, type **service.msc** and press **ENTER** to open the **Services** MMC snap-in.  
  
3.  Open the **Properties** dialog box for the service you created. Right-click the service and select **Properties**.  
  
4.  Click the **Log On** tab, select **This Account**, and then enter the logon name used for the isolated host instance.  
  
5.  Click **OK**.  
  
6.  Manually start the service to load the user profile for that logon user.  
  
### The Key Usage attribute of a certificate must match the certificate's use  
 Certificates used for AS2 transport must have the attributes required for their intended use. For signing and signature verification, the Key Usage attribute of the certificate must be Digital Signature. For encryption and decryption, the Key Usage attribute of the certificate must be Data Encipherment or Key Encipherment. You can verify the Key Usage attribute by double-clicking the certificate, clicking the **Details** tab in the **Certificate** dialog box, and checking the **Key Usage** field.  
  
### The certificate resolution list will be verified for an outgoing MDN if the AS2-To property is not set for the party  
 In the default agreement for an outgoing MDN, the certificate resolution list verification is performed. If you do not want this verification to be performed, verify that the correct AS2-To party property is set, so the receiving party can be resolved and the party properties can be determined. If so, the default agreement that prompts verification of the certificate resolution list will not be used. You will also need to disable the Check Certification Revocation List property on the General page of the AS2 party properties.