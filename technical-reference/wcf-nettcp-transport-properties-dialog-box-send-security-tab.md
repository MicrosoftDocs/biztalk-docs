---
title: WCF-NetTcp Transport Properties Dialog Box, Send, Security Tab
TOCTitle: WCF-NetTcp Transport Properties Dialog Box, Send, Security Tab
ms:assetid: 810353fe-051b-4c2d-a31c-19e8ce7a7289
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb226379(v=BTS.80)
ms:contentKeyID: 51529277
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-nettcp.transport.send.security
---

# WCF-NetTcp Transport Properties Dialog Box, Send, Security Tab

 

Use the **Security** tab to define the security capabilities of the WCF-NetTcp send adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Security mode</strong></td>
<td>Specify the type of security that is used. Valid values include the following:<br />
<br />
- <strong>None</strong>: Messages are not secured during transfer.<br />
- <strong>Transport</strong>: Transport security is provided using <strong>TLS over TCP</strong> or <strong>SPNego</strong>. It is possible to control the protection level with this mode.<br />
- <strong>Message</strong>: Security is provided using SOAP message security. By default, the SOAP <strong>Body</strong> is encrypted and signed. This mode offers a variety of features, such as whether the service credentials are available at the client out of band, and the algorithm suite to use.<br />
- <strong>TransportWithMessageCredential</strong>: Transport security is coupled with message security. Transport security is provided by <strong>TLS over TCP</strong>, or <strong>SPNego</strong>, and ensures integrity, confidentiality, and server authentication. SOAP message security provides client authentication. To use this mode, the CA certificate chain for the service's X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port. <strong>Note:</strong> This security mode cannot be used with the <strong>Transport client credential type</strong> property, <strong>None</strong>.<br />
<br />
The default is <strong>Transport</strong>.</td>
</tr>
<tr class="even">
<td><strong>Transport client credential type</strong></td>
<td>Specify the type of credential to be used when performing the send port authentication. Valid values include the following:<br />
<br />
- <strong>None</strong>: No authentication occurs at the transport level. This credential type supports only <strong>EncryptAndSign</strong> for the <strong>Transport protection level</strong> property. The CA certificate chain for the service's X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port.<br />
- <strong>Windows</strong>: Windows integrated authentication of the client using SP Negotiation (Kerberos negotiation). The user account under which this send port runs is used for services to authenticate this send port.You must configure the <strong>User principal name</strong> property to the user account name running the destination service by using the <strong>Identity Editor</strong> dialog box.<br />
- <strong>Certificate</strong>: Client authentication using the client certificate specified through the <strong>Client certificate - Thumbprint</strong> property. This uses SSL Negotiation. This credential type supports only the <strong>EncryptAndSign</strong> for the <strong>Transport protection level</strong> property. The CA certificate chain for the service X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port.<br />
<br />
The default is <strong>Windows</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Transport protection level</strong></td>
<td>Define security at the level of the TCP transport. Signing messages mitigates the risk of a third party tampering with the message while it is being transferred. Encryption provides data-level privacy during transport. Valid values include the following:<br />
<br />
- <strong>None</strong>: No protection.<br />
- <strong>Sign</strong>: Messages are signed.<br />
- <strong>EncryptAndSign</strong>: Messages are encrypted and signed.<br />
<br />
The default value is <strong>EncryptAndSign</strong>.</td>
</tr>
<tr class="even">
<td><strong>Message client credential type</strong></td>
<td>Specify the type of credential to be used when performing client authentication using message-based security. Valid values include the following:<br />
<br />
- <strong>None</strong>: This allows the service to interact with anonymous clients. This indicates that this send port does not provide any client credential. The CA certificate chain for the service X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port.<br />
- <strong>Windows</strong>: Allow the SOAP exchanges to be under the authenticated context of a Windows credential. The user account under which this send port runs is used for services to authenticate this send port. The client credential is passed through the SOAP <strong>Header</strong> element using the <strong>WSS SOAP Message Security Kerberos Token Profile 1.0</strong> protocol. You must configure the <strong>User principal name</strong> property to the user account name running the destination service by using the <strong>Identity Editor</strong> dialog box.<br />
- <strong>UserName</strong>: This send port is authenticated to services with a <strong>UserName</strong> credential. The credential is passed through the SOAP <strong>Header</strong> element using the <strong>WSS SOAP Message Security UsernameToken Profile 1.0</strong> protocol. This option requires configuring the <strong>Client credentials</strong> property. The CA certificate chain for the service X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port.<br />
- <strong>Certificate</strong>: This send port is authenticated to services using the client certificate specified through the <strong>Client certificate - Thumbprint</strong> property. The credential is passed through the SOAP <strong>Header</strong> element using the <strong>WSS SOAP Message Security X509 Token Profile 1.0</strong> protocol. The CA certificate chain for the service X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port.<br />
<br />
The default is <strong>Windows</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Algorithm suite</strong></td>
<td>Specify the message encryption and key-wrap algorithms. These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification. Possible values are:<br />
<br />
- <strong>Basic128</strong>: Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>Basic128Rsa15</strong>: Use Aes128 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />
- <strong>Basic128Sha256</strong>: Use Aes256 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>Basic128Sha256Rsa15</strong>: Use Aes128 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />
- <strong>Basic192</strong>: Use Aes192 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>Basic192Rsa15</strong>: Use Aes192 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />
- <strong>Basic192Sha256</strong>: Use Aes192 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>Basic192Sha256Rsa15</strong>: Use Aes192 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />
- <strong>Basic256</strong>: Use Aes256 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>Basic256Rsa15</strong>: Use Aes256 for message encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />
- <strong>Basic256Sha256</strong>: Use Aes256 for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>Basic256Sha256Rsa15</strong>: Use Aes256 for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />
- <strong>TripleDes</strong>: Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.<br />
- <strong>TripleDesRsa15</strong>: Use TripleDes encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />
- <strong>TripleDesSha256</strong>: Use TripleDes for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>TripleDesSha256Rsa15</strong>: Use TripleDes for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />
<br />
The default value is <strong>Basic256</strong>.</td>
</tr>
<tr class="even">
<td><strong>Client certificate -Thumbprint</strong></td>
<td>Specify the thumbprint of the X.509 certificate for authenticating this send port to a service. The thumbprint can be selected by navigating the <strong>My</strong> store in the <strong>Current User</strong> location with the <strong>Browse</strong> button. <strong>Note:</strong> You must install the client certificate into the <strong>Current User</strong> location of the user account for the send handler hosting this send port.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 40<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>Client credentials</strong></td>
<td>Specify the credentials for sending messages when using <strong>UserName</strong> for the <strong>Message client credential type</strong> property. You can specify the property by clicking the <strong>Edit Credentials</strong> button.<br />
<br />
The default value is <strong>Do not use Single Sign-On</strong>.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-NetTcp Send Port](https://msdn.microsoft.com/library/bb226460\(v=bts.80\))  
[Installing Certificates for the WCF Adapters](https://msdn.microsoft.com/library/bb245944\(v=bts.80\))

