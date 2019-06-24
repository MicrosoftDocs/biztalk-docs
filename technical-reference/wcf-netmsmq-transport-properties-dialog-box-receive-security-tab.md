---
title: WCF-NetMsmq Transport Properties Dialog Box, Receive, Security Tab
TOCTitle: WCF-NetMsmq Transport Properties Dialog Box, Receive, Security Tab
ms:assetid: d1a533c0-5345-4949-aa14-5e20013df65b
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226546(v=BTS.80)
ms:contentKeyID: 51531526
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcr-netmsmq.transport.receive.security
---

# WCF-NetMsmq Transport Properties Dialog Box, Receive, Security Tab

 

Use the **Security** tab to define the security capabilities of the WCF-NetMsmq receive adapter.

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
- <strong>Message</strong>: Specify the end-to-end application security. There is no security offered at the transport layer. This is similar to the security offered by other standard bindings. To use this security mode, the service certificate for this receive location must be provided through the <strong>Service certificate - Thumbprint</strong> property.<br />
- <strong>Both</strong>: Offer security at both the transport and SOAP messaging layer. To use this security mode, the service certificate for this receive location must be provided through the <strong>Service certificate - Thumbprint</strong> property.<br />
<br />
The default is <strong>Transport</strong>.</td>
</tr>
<tr class="even">
<td><strong>MSMQ authentication mode</strong></td>
<td>Specify how the message must be authenticated by the MSMQ transport. Valid values include the following:<br />
<br />
- <strong>None</strong>: No authentication. If this authentication mode is used, the <strong>MSMQ protection level</strong> property must be set to <strong>None</strong>.<br />
- <strong>WindowsDomain</strong>: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message. This is then used to check the ACL of the queue to ensure the user has write permission for the queue. If this authentication mode is used, the <strong>MSMQ protection level</strong> property cannot be set to <strong>None</strong>. To use this authentication mode, you must enable <strong>Active Directory Integration</strong> for <strong>MSMQ</strong>.<br />
- <strong>Certificate</strong>: This send port retrieves the certificate from the certificate store. If this authentication mode is used, the <strong>MSMQ protection level</strong> property cannot be set to <strong>None</strong>. You must install the CA certificate chain for the client certificates in the Trusted Root Certification Authorities certificate store of this computer.<br />
- The default is <strong>WindowsDomain</strong>.</td>
</tr>
<tr class="odd">
<td><strong>MSMQ protection level</strong></td>
<td>Specify the way messages are secured at the level of the MSMQ transport. Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation. Valid values include the following:<br />
<br />
- <strong>None</strong>: No protection.<br />
- <strong>Sign</strong>: Messages are signed.<br />
- <strong>EncryptAndSign</strong>: Messages are encrypted and signed. To use this protection level, you must enable <strong>Active Directory Integration</strong> for <strong>MSMQ</strong>.<br />
- The default is <strong>Sign</strong>.</td>
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
- <strong>None</strong>: Allow this receive location to interact with anonymous clients. This indicates that clients do not provide any client credentials to this receive location.<br />
- <strong>Windows</strong>: Allow the SOAP exchanges to be under the authenticated context of a Windows credential. You must create the domain or local user accounts corresponding to client credentials. This always performs Kerberos-based authentication.<br />
- <strong>UserName</strong>: Allow this receive location to require that clients be authenticated using a <strong>UserName</strong> credential. You must create the domain or local user accounts corresponding to the client credentials. WCF does not support sending a password digest or deriving keys using password and using such keys for message security. Therefore, WCF enforces that the exchange is secured when using <strong>UserName</strong> credentials.<br />
- <strong>Certificate</strong>: Allow this receive location to require that a client be authenticated using a certificate. In addition, you must install the CA certificate chain for the client certificate in the Trusted Root Certification Authorities certificate store of this computer.<br />
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
- <strong>TripleDes</strong>: Use TripleDes encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>TripleDesRsa15</strong>: Use TripleDes encryption, Sha1 for message digest, and Rsa15 for key wrap.<br />
- <strong>TripleDesSha256</strong>: Use TripleDes for message encryption, Sha256 for message digest, and Rsa-oaep-mgf1p for key wrap.<br />
- <strong>TripleDesSha256Rsa15</strong>: Use TripleDes for message encryption, Sha256 for message digest, and Rsa15 for key wrap.<br />
<br />
The default value is <strong>Basic256</strong>.</td>
</tr>
<tr class="even">
<td><strong>Service certificate -Thumbprint</strong></td>
<td>Specify the thumbprint of the X.509 certificate for this receive location that the clients use to authenticate the service. You can select the thumbprint by navigating the <strong>My</strong> store in the <strong>Current User</strong> location with the <strong>Browse</strong> button. <strong>Note:</strong> You must install the service certificate into the <strong>Current User</strong> location of the user account for the receive handler hosting this receive location.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 40<br />
<br />
The default is an empty string.</td>
</tr>
</tbody>
</table>


## See Also

[Managing BizTalk Hosts and Host Instances](https://msdn.microsoft.com/library/aa561042\(v=bts.80\))  
[How to Change Service Accounts and Passwords](https://msdn.microsoft.com/library/aa561505\(v=bts.80\))  
[Message Queuing and Active Directory](http://go.microsoft.com/fwlink/?linkid=193602)  
[How to Configure a WCF-NetMsmq Receive Location](https://msdn.microsoft.com/library/bb259976\(v=bts.80\))  
[Installing Certificates for the WCF Adapters](https://msdn.microsoft.com/library/bb245944\(v=bts.80\))

