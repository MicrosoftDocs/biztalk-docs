---
title: WCF-NetTcp Transport Properties Dialog Box, Receive, Security Tab
TOCTitle: WCF-NetTcp Transport Properties Dialog Box, Receive, Security Tab
ms:assetid: 51a99053-7248-498f-a3aa-62b615c364e6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb246097(v=BTS.80)
ms:contentKeyID: 51528031
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-nettcp.transport.receive.security
---

# WCF-NetTcp Transport Properties Dialog Box, Receive, Security Tab

 

Use the **Security** tab to define the security capabilities of the WCF-NetTcp receive adapter.

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
- <strong>Transport</strong>: Transport security is provided using <strong>TLS over TCP</strong> or <strong>SPNego</strong>. It is possible to control the protection level with this mode. If you select <strong>None</strong> or <strong>Certificate</strong> for the <strong>Transport client credential type</strong> property in this security mode, you must supply the service certificate for this receive location through the <strong>Service certificate - Thumbprint</strong> property.<br />
- <strong>Message</strong>: Security is provided using SOAP message security. By default, the SOAP <strong>Body</strong> is encrypted and signed. This mode offers a variety of features, such as whether the service credentials are available at the client out of band, and the algorithm suite to use. If you select <strong>None</strong>, <strong>UserName</strong>, or <strong>Certificate</strong> for the <strong>Message client credential type</strong> property in this security mode, you must supply the service certificate for this receive location through the <strong>Service certificate - Thumbprint</strong> property.<br />
- <strong>TransportWithMessageCredential</strong>: Transport security is coupled with message security. Transport security is provided by <strong>TLS over TCP</strong> or <strong>SPNego</strong> and ensures integrity, confidentiality, and server authentication. If you select <strong>Windows</strong>, <strong>UserName</strong>, or <strong>Certificate</strong> for the <strong>Message client credential type</strong> property in this security mode, you must supply the service certificate for this receive location through the <strong>Service certificate - Thumbprint</strong> property. <strong>Note:</strong> This security mode cannot be used with the <strong>Transport client credential type</strong> property, <strong>None</strong>.<br />
<br />
The default is <strong>Transport</strong>.</td>
</tr>
<tr class="even">
<td><strong>Transport client credential type</strong></td>
<td>Specify the type of credential to be used when performing the client authentication. Valid values include the following:<br />
<br />
- <strong>None</strong>: No authentication occurs at the transport level. This credential type supports only <strong>EncryptAndSign</strong> for the <strong>Transport protection level</strong> property.<br />
- <strong>Windows</strong>: Windows integrated authentication of the client using SP Negotiation (Kerberos negotiation). You must create the domain or local user accounts corresponding to client credentials. In addition, the client's <strong>userPrincipalName</strong> element must be configured with the user account name running this receive handler.<br />
- <strong>Certificate</strong>: Client authentication using client certificates. To authenticate the client certificates, the CA certificate chain for the client certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer. This credential type supports only <strong>EncryptAndSign</strong> for the <strong>Transport protection level</strong> property.<br />
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
- <strong>None</strong>: This allows the service to interact with anonymous clients. This indicates that this client does not provide any client credential.<br />
- <strong>Windows</strong>: Allow the SOAP exchanges to be under the authenticated context of a Windows credential. The client credential is passed through the SOAP <strong>Header</strong> element using the <strong>WSS SOAP Message Security Kerberos Token Profile 1.0</strong> protocol. You must create the domain or local user accounts corresponding to client credentials. In addition, the client's <strong>userPrincipalName</strong> element must be configured with the user account name running this receive handler.<br />
- <strong>UserName</strong>: Clients are authenticated to this receive location with a <strong>UserName</strong> credential. The credential is passed through the SOAP <strong>Header</strong> element using the <strong>WSS SOAP Message Security UsernameToken Profile 1.0</strong> protocol. You must create the domain or local user accounts corresponding to client credentials.<br />
- <strong>Certificate</strong>: Clients are authenticated to this receive location using the client certificate specified through the <strong>Service certificate - Thumbprint</strong> property. The credential is passed through the SOAP <strong>Header</strong> element using the <strong>WSS SOAP Message Security X509 Token Profile 1.0</strong> protocol. To authenticate the client certificates, the CA certificate chain for the client certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer. In addition, you must provide the service certificate for this location through the <strong>Service certificate - Thumbprint</strong> property.<br />
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
<td><strong>Service certificate -Thumbprint</strong></td>
<td>Specify the thumbprint of the X.509 certificate for this receive location that the clients use to authenticate the service. The thumbprint can be selected by navigating the <strong>My</strong> store in the <strong>Current User</strong> location with the <strong>Browse</strong> button. <strong>Note:</strong> You must install the service certificate into the <strong>Current User</strong> location of the user account for the receive handler hosting this receive location.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 40<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>Use Single Sign-On</strong></td>
<td>Specify whether to use Single Sign-On to retrieve client credentials to issue an SSO ticket. This option is valid only for the security configurations listed in the following section, &quot;Enterprise Single Sign-On Supportability for the WCF -NetTcp Receive Adapter.&quot;<br />
<br />
The default value is cleared.</td>
</tr>
</tbody>
</table>


## Enterprise Single Sign-On Supportability for the WCF-NetTcp Receive Adapter.

The WCF-NetTcp receive adapter can issue an SSO ticket from the SSO server only in the security configurations shown in the following table.

<table>
<thead>
<tr class="header">
<th><strong>Security mode</strong></th>
<th><strong>Transport client credential type</strong></th>
<th><strong>Message client credential type</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Transport</strong></td>
<td><strong>Windows</strong></td>
<td>N/A</td>
</tr>
<tr class="even">
<td><strong>Message</strong></td>
<td>N/A</td>
<td><strong>Windows</strong></td>
</tr>
<tr class="odd">
<td><strong>Message</strong></td>
<td>N/A</td>
<td><strong>UserName</strong></td>
</tr>
<tr class="even">
<td><strong>TransportWithMessageCredential</strong></td>
<td>N/A</td>
<td><strong>Windows</strong></td>
</tr>
<tr class="odd">
<td><strong>TransportWithMessageCredential</strong></td>
<td>N/A</td>
<td><strong>UserName</strong></td>
</tr>
</tbody>
</table>


## See Also

[Managing BizTalk Hosts and Host Instances](https://msdn.microsoft.com/en-us/library/aa561042\(v=bts.80\))  
[How to Change Service Accounts and Passwords](https://msdn.microsoft.com/en-us/library/aa561505\(v=bts.80\))  
[How to Configure a WCF-NetTcp Receive Location](https://msdn.microsoft.com/en-us/library/bb226412\(v=bts.80\))  
[Installing Certificates for the WCF Adapters](https://msdn.microsoft.com/en-us/library/bb245944\(v=bts.80\))

