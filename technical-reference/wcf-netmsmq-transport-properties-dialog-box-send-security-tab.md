---
title: WCF-NetMsmq Transport Properties Dialog Box, Send, Security Tab
TOCTitle: WCF-NetMsmq Transport Properties Dialog Box, Send, Security Tab
ms:assetid: 35d394bb-d719-4280-9f70-9deb46cae097
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246035(v=BTS.80)
ms:contentKeyID: 51527320
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netmsmq.transport.send.security
---

# WCF-NetMsmq Transport Properties Dialog Box, Send, Security Tab

 

Use the **Security** tab to define the security capabilities of the WCF-NetMsmq send adapter.

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
- <strong>Transport</strong>: Protection and authentication are offered by the transport. This applies to communication between the two queue managers. There is no security offered between the application and queue manager. Existing MSMQ applications are functionally equivalent with this type of security mode.<br />
- <strong>Message</strong>: Specify the end-to-end application security. There is no security offered at the transport layer. This is similar to the security offered by other standard bindings. To use this security mode, the send port needs to be provisioned with the service certificate. The service credential can be provided through the <strong>Service certificate - Thumbprint</strong> property.<br />
- <strong>Both</strong>: Offer security at both the transport and SOAP messaging layer. To use this security mode, the send port needs to be provisioned with the service certificate. The service credential can be provided through the <strong>Service certificate - Thumbprint</strong> property.<br />
- The default is <strong>Transport</strong>.</td>
</tr>
<tr class="even">
<td><strong>MSMQ authentication mode</strong></td>
<td>Specify how the message must be authenticated by the MSMQ transport. Valid values include the following:<br />
<br />
- <strong>None</strong>: No authentication. If this authentication mode is used, the <strong>MSMQ protection level</strong> property must be set to <strong>None</strong>.<br />
- <strong>WindowsDomain</strong>: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message. This is then used to check the ACL of the queue to ensure the user has write permission for the queue. If this authentication mode is used, the <strong>MSMQ protection level</strong> property cannot be set to <strong>None</strong>. To use this authentication mode, you must enable <strong>Active Directory Integration</strong> for <strong>MSMQ</strong>.<br />
- <strong>Certificate</strong>: This send port retrieves the certificate from the certificate store to authenticate this send port to services. If this authentication mode is used, the <strong>MSMQ protection level</strong> property cannot be set to <strong>None</strong>, and the <strong>Client certificate - Thumbprint</strong> property must be set.<br />
- The default is <strong>WindowsDomain</strong>.</td>
</tr>
<tr class="odd">
<td><strong>MSMQ protection level</strong></td>
<td>Specify the way messages are secured at the level of the MSMQ transport. Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation. Valid values include the following:<br />
<br />
- <strong>None</strong>: No protection.<br />
- <strong>Sign</strong>: Messages are signed.<br />
- <strong>EncryptAndSign</strong>: Messages are encrypted and signed. To use this protection level, you must enable <strong>Active Directory Integration</strong> for <strong>MSMQ</strong>.<br />
<br />
The default is <strong>Sign</strong>.</td>
</tr>
<tr class="even">
<td><strong>Secure hash algorithm</strong></td>
<td>Specify the hash algorithm to be used for computing the message digest. This property is not available if the <strong>MSMQ protection level</strong> property is set to <strong>None</strong>. Valid values include the following:<br />
<br />
- <strong>MD5</strong><br />
- <strong>SHA1</strong><br />
- <strong>SHA256</strong><br />
- <strong>SHA512</strong><br />
<br />
The default is <strong>SHA1</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Encryption algorithm</strong></td>
<td>Specify the algorithm to be used for message encryption on the wire when transferring messages between message queue managers. This property is available only if the <strong>MSMQ protection level</strong> property is set to <strong>EncryptAndSign</strong>. Valid values include the following:<br />
<br />
- <strong>RC4Stream</strong><br />
- <strong>AES</strong><br />
<br />
The default value is <strong>RC4Stream</strong>.</td>
</tr>
<tr class="even">
<td><strong>Message client credential type</strong></td>
<td>Specify the type of credential to be used when performing client authentication using the message-based security. Valid values include the following:<br />
<br />
- <strong>None</strong>: Allow the service to interact with anonymous clients. This indicates that this send port does not provide any client credential.<br />
- <strong>Windows</strong>: Allow the SOAP exchanges to be under the authenticated context of a Windows credential. This always performs Kerberos-based authentication.<br />
- <strong>UserName</strong>: Allow the service to require that this send port be authenticated using a <strong>UserName</strong> credential. This credential needs to be specified through the <strong>Client credentials</strong> property. WCF does not support sending a password digest or deriving keys using password and using such keys for message security. Therefore, WCF enforces that the exchange is secured when using <strong>UserName</strong> credentials.<br />
- <strong>Certificate</strong>: Allow the service to require that the client be authenticated using a certificate. The client credential in this case needs to be specified using the <strong>Client certificate - Thumbprint</strong> property.<br />
<br />
The default value is <strong>Windows</strong>.</td>
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
<td><strong>Client certificate - Thumbprint</strong></td>
<td>Specify the thumbprint of the X.509 certificate for authenticating this send port to a service. You can select the thumbprint by navigating to the <strong>My</strong> store in the <strong>Current User</strong> location with the <strong>Browse</strong> button. <strong>Note:</strong> You must install the client certificate into the <strong>Current User</strong> location of the user account for the send handler hosting this send port.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 40<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>Service certificate - Thumbprint</strong></td>
<td>Specify the thumbprint of the X.509 certificate for authenticating the service to which this send port sends messages. You can select the thumbprint by navigating to the <strong>Other People</strong> store in the <strong>Local Computer</strong> location with the <strong>Browse</strong> button. In addition, the CA certificate chain for the service X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 40<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Client credentials</strong></td>
<td>Specify the credentials for sending messages when using <strong>UserName</strong> for the <strong>Message client credential type</strong> property. You can specify this property by clicking the <strong>Edit Credentials</strong> button.<br />
<br />
The default value is <strong>Do not use Single Sign-On</strong>.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-NetMsmq Send Port](https://msdn.microsoft.com/library/bb245965\(v=bts.80\))
[Installing Certificates for the WCF Adapters](https://msdn.microsoft.com/library/bb245944\(v=bts.80\))
[Managing BizTalk Hosts and Host Instances](https://msdn.microsoft.com/library/aa561042\(v=bts.80\))
[How to Change Service Accounts and Passwords](https://msdn.microsoft.com/library/aa561505\(v=bts.80\))
[Message Queuing and Active Directory](https://go.microsoft.com/fwlink/?linkid=193602)

