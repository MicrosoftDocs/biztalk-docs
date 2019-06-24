---
title: WCF Adapters Transport Properties Dialog Box, General Tab, Identity Editor
TOCTitle: WCF Adapters Transport Properties Dialog Box, General Tab, Identity Editor
ms:assetid: 47a04277-71a9-4bc3-b2bb-67aa61007656
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246073(v=BTS.80)
ms:contentKeyID: 51527721
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-adapters.transport.general.identity
---

# WCF Adapters Transport Properties Dialog Box, General Tab, Identity Editor

 

Use the **Identity Editor** dialog box to configure the identity of the service that this send port expects. These settings enable this send port to authenticate the service. In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element. The values that can be specified for the **Endpoint Identity** property differ according to the security configuration on the **Security** tab. For more information about how to setup the **Identity** property for WCF services, see "Specifying the Identity of a Service for Authentication" listed in the See Also section of this topic.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>1. DNS</strong></td>
<td>Specify a DNS identity of the service to which this send port sends messages.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>2. Service principal name</strong></td>
<td>Specify a server principal name (SPN) identity, which is the principal name to uniquely identify an instance of the service to which this send port sends messages.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>3. User principal name</strong></td>
<td>Specify a user principal name (UPN) identity, which is the logon name type of a user on a network. The user principal name consists of the user object name used in Active Directory, followed by the at symbol (@) and then, typically, the Domain Name System parent domain. For example, JeffSmith in the Fabrikam.com domain tree might have the user principal name jeffsmith@fabrikam.com.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>4. RSA</strong></td>
<td>Specify the RSA public key value of an X.509 certificate used to authenticate the service to which this send port sends messages. An RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or your own RSA key value. This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>5. Certificate (Base-64)</strong></td>
<td>Specify a Base64 encoding of an X.509 certificate used to validate the service that this send port consumes.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Find type</strong></td>
<td>Specify the type of X.509 search to be executed. The type contained in the <strong>Find value</strong> property must satisfy the requirements of the specified <strong>Find type</strong> value. Valid values include the following:<br />
<br />
- <strong>FindByThumbPrint</strong><br />
- <strong>FindBySubjectName</strong><br />
- <strong>FindBySubjectDistinguishedName</strong><br />
- <strong>FindByIssuerName</strong><br />
- <strong>FindByIssuerDistinguishedName</strong><br />
- <strong>FindBySerialNumber</strong><br />
- <strong>FindByTimeValid</strong><br />
- <strong>FindByTimeNotYetValid</strong><br />
- <strong>FindByTimeExpired</strong><br />
- <strong>FindByTemplateName</strong><br />
- <strong>FindByApplicationPolicy</strong><br />
- <strong>FindByCertificatePolicy</strong><br />
- <strong>FindByExtension</strong><br />
- <strong>FindByKeyUsage</strong><br />
- <strong>FindBySubjectKeyIdentifier</strong><br />
<br />
The default value is <strong>FindBySubjectDistinguishedName</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Find value</strong></td>
<td>Specify the value to search for in the X.509 certificate store. The type contained in this property must satisfy the requirements of the specified <strong>Find type</strong> value.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Is chain included?</strong></td>
<td>A Boolean value that specifies if the validation is done using a certificate chain.<br />
<br />
The default is <strong>False</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Store location</strong></td>
<td>Specify the location of the certificate store that this send port can use to validate the service. Valid values include the following:<br />
<br />
- <strong>LocalMachine</strong>: The certificate store assigned to the local machine.<br />
- <strong>CurrentUser</strong>: The certificate store assigned to the current user. <strong>Note:</strong> To use the <strong>CurrentUser</strong> location, you must install the certificate into the <strong>Current User</strong> location of the user account configured for the send handler hosting this send port.<br />
<br />
The default value is <strong>LocalMachine</strong>.</td>
</tr>
<tr class="even">
<td><strong>Store name</strong></td>
<td>Specify the name of the X.509 certificate store to open.<br />
<br />
Valid values include the following:<br />
<br />
- <strong>AddressBook</strong>: Certificate store for other users.<br />
- <strong>AuthRoot</strong>: Certificate store for third-party certification authorities (CAs).<br />
- <strong>CertificateAuthority</strong>: Certificate store for intermediate CAs.<br />
- <strong>Disallowed</strong>: Certificate store for revoked certificates.<br />
- <strong>My</strong>: Certificate store for personal certificates.<br />
- <strong>Root</strong>: Certificate store for trusted root CAs.<br />
- <strong>TrustedPeople</strong>: Certificate store for directly trusted people and resources.<br />
- <strong>TrustedPublisher</strong>: Certificate store for directly trusted publishers.<br />
<br />
The default value is <strong>My</strong>.</td>
</tr>
</tbody>
</table>


## How to Remove an Identity Setting

To remove an identity setting for a send port, delete all the values of the **1. DNS**, **2. Service principal name**, **3. User principal name**, **4. RSA**, **5. Certificate (Base-64)**, and **Find value** properties.

## See Also

[The \<identity\> element](http://go.microsoft.com/fwlink/?linkid=75747)  
[Managing BizTalk Hosts and Host Instances](https://msdn.microsoft.com/library/aa561042\(v=bts.80\))  
[How to Change Service Accounts and Passwords](https://msdn.microsoft.com/library/aa561505\(v=bts.80\))  
[Specifying the Identity of a Service for Authentication](http://go.microsoft.com/fwlink/?linkid=88889)

