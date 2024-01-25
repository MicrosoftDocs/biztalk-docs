---
description: "Learn more about: Single Sign-On Support for the WCF Adapters"
title: "Single Sign-On Support for the WCF Adapters"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Single Sign-On Support for the WCF Adapters
You can configure Enterprise Single Sign-On (SSO) for use with a WCF receive location or send port by using the BizTalk Administration console. This topic describes how SSO works with the WCF adapters.

 In an enterprise environment, where a user interacts with various systems and applications, it is likely that the environment does not maintain the user context through multiple processes, products, and computers. This user context is crucial to providing single sign-on capabilities, because it is necessary to verify who initiated the original request. To overcome this problem Enterprise Single Sign-On (SSO) provides an SSO ticket (not a Kerberos ticket) that applications can use to get the credentials that correspond to the user who made the original request.

 When a receive adapter gets a message, the adapter can request an SSO ticket from an SSO server. This encrypted ticket contains the [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] identity of the user that made the request and a time-out period. After the ticket is acquired, it is added as a property to the incoming message. When a send adapter transmits a message, the adapter contacts an SSO server with the issued SSO ticket and an affiliate application name for which the adapter is trying to retrieve a credential. The SSO server looks up the user credential for the target affiliate application, and then returns the credential to the send adapter, which uses it to send an appropriately authenticated message to the affiliate application.

## Single Sign-On Support for the WCF Receive Locations
 The applied security settings combined with the type of a WCF adapter used for a receive location decide whether the WCF receive adapter can issue SSO tickets. For the WCF receive adapter to issue an SSO token, WCF clients have to send a credential that the adapter can impersonate. Impersonation is the ability of a server application to take on the identity of the client. The credential must map to a valid [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] user account for proper impersonation.

> [!NOTE]
>  For the security settings and the WCF adapters that do not demand the clients to send credentials for impersonation, you can issue SSO tickets with any type of credentials that the clients send in a custom receive pipeline component. For more information about how to handle SSO tickets in receive pipeline components, see the sample pipeline component, InPipelineComp, included in [File Inventory for the Service Oriented Solution](../core/file-inventory-for-the-service-oriented-solution.md).

 **Single Sign-On Support for the WCF-BasicHttp Receive Location**

 The WCF-BasicHttp receive adapter can issue an SSO ticket from the SSO server only in the security configurations shown in the following table.

> [!NOTE]
>  For more information about mapping a certificate to a [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] user account, see "Mapping certificates to user accounts" at [https://go.microsoft.com/fwlink/?LinkId=87478](/previous-versions/windows/it-pro/windows-server-2003/cc779393(v=ws.10)).

|Security mode|Transport client credential type|Message client credential type|
|-------------------|--------------------------------------|------------------------------------|
|Transport|Basic|N/A|
|Transport|Digest|N/A|
|Transport|Ntlm|N/A|
|Transport|Windows|N/A|
|Transport|Certificate|N/A|
|Message|N/A|UserName|
|Message|N/A|Certificate|
|TransportWithMessageCredential|N/A|Certificate|
|TransportWithMessageCredential|N/A|UserName|
|TransportCredentialOnly|Basic|N/A|
|TransportCredentialOnly|Digest|N/A|
|TransportCredentialOnly|Ntlm|N/A|
|TransportCredentialOnly|Windows|N/A|
|TransportCredentialOnly|Certificate|N/A|

 **Single Sign-On Support for the WCF-WSHttp Receive Location**

 The WCF-WSHttp receive adapter can issue an SSO ticket from the SSO server only in the security configurations shown in the following table.

|Security mode|Transport client credential type|Message client credential type|
|-------------------|--------------------------------------|------------------------------------|
|Transport|Basic|N/A|
|Transport|Digest|N/A|
|Transport|Ntlm|N/A|
|Transport|Windows|N/A|
|Transport|Certificate|N/A|
|Message|N/A|UserName|
|Message|N/A|Windows|
|Message|N/A|Certificate|
|TransportWithMessageCredential|N/A|Windows|
|TransportWithMessageCredential|N/A|Certificate|
|TransportWithMessageCredential|N/A|UserName|

 **Single Sign-On Support for the WCF-NetTcp Receive Location**

 The WCF-NetTcp receive adapter can issue an SSO ticket from the SSO server only in the security configurations shown in the following table.

|Security mode|Transport client credential type|Message client credential type|
|-------------------|--------------------------------------|------------------------------------|
|Transport|Windows|N/A|
|Transport|Certificate|N/A|
|Message|N/A|Certificate|
|Message|N/A|Windows|
|Message|N/A|UserName|
|TransportWithMessageCredential|N/A|Certificate|
|TransportWithMessageCredential|N/A|Windows|
|TransportWithMessageCredential|N/A|UserName|

 S**ingle Sign-On Support for the WCF-NetNamedPipe Receive Location**

 The WCF-NetNamedPipe receive adapter can issue an SSO ticket from the SSO server only in the security configurations shown in the following table.

|Security mode|Transport client credential type|Message client credential type|
|-------------------|--------------------------------------|------------------------------------|
|Transport|N/A|N/A|

 **Single Sign-On Support for the WCF-Custom and the WCF-CustomIsolated Receive Location**

 For the WCF-Custom and WCF-CustomIsolated receive locations to issue SSO tickets, the security settings used in the receive locations require the WCF clients to send credentials that can be impersonated by Windows Communication Foundation. WCF supports impersonation for various types of client credentials. For more information about the credential types that WCF supports for impersonation, see "Delegation and Impersonation with WCF" at [https://go.microsoft.com/fwlink/?LinkId=87476](/dotnet/framework/wcf/feature-details/delegation-and-impersonation-with-wcf).

## Single Sign-On Support for the WCF Send Ports
 For the WCF send ports, you can specify an affiliate application name to use for SSO only in the security configurations shown in the following table.

|Security mode|Transport client credential type|Message client credential type|
|-------------------|--------------------------------------|------------------------------------|
|Transport|Digest|N/A|
|Transport|Basic|N/A|
|Message|N/A|UserName|

> [!NOTE]
>  For a WCF send port to validate and redeem an SSO ticket properly, the **SSOTicket** and **OriginatorSID** context properties must be available in a message to be sent. A receive location with Single Sign-On enabled can promote these properties from a sender's [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] account.

## See Also
 [Enterprise Single Sign-On](../core/enterprise-single-sign-on2.md)