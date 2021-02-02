---
description: "Learn more about: WCF-BasicHttp Transport Properties Dialog Box, Send, Security Tab"
title: WCF-BasicHttp Transport Properties Dialog Box, Send, Security Tab
TOCTitle: WCF-BasicHttp Transport Properties Dialog Box, Send, Security Tab
ms:assetid: c3f47362-fb58-4d56-82e4-a79f6e3bdc26
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226514(v=BTS.80)
ms:contentKeyID: 51531140
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-basichttp.transport.send.security
---

# WCF-BasicHttp Transport Properties Dialog Box, Send, Security Tab

 

Use the **Security** tab to define the security capabilities of the WCF-BasicHttp send adapter.

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
- <strong>Transport</strong>: Security is provided using the HTTPS transport. The SOAP messages are secured using HTTPS. The CA certificate chain for the service's X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the service can be authenticated to the send port using the service's certificate.<br />
- <strong>Message</strong>: Security is provided using SOAP message security. By default, the SOAP <strong>Body</strong> element is encrypted and signed. The only valid <strong>Message client credential type</strong> for the WCF-BasicHttp send adapter is <strong>Certificate</strong>. This mode requires the HTTP transport.<br />
- <strong>TransportWithMessageCredential</strong>: Integrity, confidentiality, and service authentication are provided by the HTTPS transport. The CA certificate chain for the service's X.509 certificate must be installed in the Trusted Root Certification Authorities certificate store on this computer so that the service can be authenticated to the send port using the service's certificate. The send port authentication is provided by SOAP message security.<br />
- <strong>TransportCredentialOnly</strong>: This mode does not provide message integrity and confidentiality. It provides HTTP-based client authentication. This mode should be used with caution. It should be used in environments where the transport security is provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.<br />
<br />
The default is <strong>None</strong>.</td>
</tr>
<tr class="even">
<td><strong>Transport client credential type</strong></td>
<td>Specify the type of credential to be used when performing the send port authentication. Valid values include the following:<br />
<br />
- <strong>None</strong>: No authentication occurs at the transport level.<br />
- <strong>Basic</strong>: Basic authentication. In Basic authentication, user names and passwords are sent in plain text over the network. This option requires configuring the <strong>Client credentials</strong> property.<br />
- <strong>Digest</strong>: Digest authentication. This authentication method operates much like Basic authentication, except that passwords are sent across the network as a hash value for additional security. Digest authentication is available only on domains with domain controllers running Windows Server operating systems authentication. This option requires configuring the <strong>Client credentials</strong> property.<br />
- <strong>Ntlm</strong>: NTLM authentication. The user account under which this send port runs is used for services to authenticate this send port.<br />
- <strong>Windows</strong>: Windows integrated authentication. The user account under which this send port runs is used for services to authenticate this send port.<br />
- <strong>Certificate</strong>: Client authentication using the client certificate specified through the <strong>Client certificate - Thumbprint</strong> property. When using this credential type, the service certificate needs to be provided through the <strong>Service certificate - Thumbprint</strong> property.<br />
<br />
The default is <strong>None</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Message client credential type</strong></td>
<td>Specify the type of credential to be used when performing client authentication using message-based security. Valid values include the following:<br />
<br />
- <strong>UserName</strong>: This send port is authenticated to the service with a <strong>UserName</strong> credential. For the WCF-BasicHttp send adapter, this is not supported.<br />
- <strong>Certificate</strong>: This send port is authenticated to services using the client certificate specified through the <strong>Client certificate - Thumbprint</strong> property. In addition, when using this credential type, the service certificate needs to be provided through the <strong>Service certificate - Thumbprint</strong> property.<br />
<br />
The default is <strong>UserName</strong>.</td>
</tr>
<tr class="even">
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
<tr class="odd">
<td><strong>Client certificate - Thumbprint</strong></td>
<td>Specify the thumbprint of the X.509 certificate for authenticating this send port to services. You can select the thumbprint by navigating to the <strong>My</strong> store in the <strong>Current User</strong> location with the <strong>Browse</strong> button. <strong>Note:</strong> You must install the client certificate into the <strong>Current User</strong> location of the user account for the send handler hosting this send port.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 40<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Service certificate - Thumbprint</strong></td>
<td>Specify the thumbprint of the X.509 certificate for authenticating the service to which this send port sends messages. You can select the thumbprint navigating to the <strong>Other People</strong> store in the <strong>Local Machine</strong> location with the <strong>Browse</strong> button.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 40<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>User name credentials</strong></td>
<td>Specify the credentials for sending messages. You can specify the property by clicking the <strong>Edit</strong> button. This option is valid only for the security configuration listed in the following section, &quot;Enterprise Single Sign-On Supportability for the WCF-BasicHttp Send Adapter.&quot;<br />
<br />
The default value is <strong>Do not use Single Sign-On</strong>.</td>
</tr>
</tbody>
</table>


## Enterprise Single Sign-On Supportability for the WCF-BasicHttp Send Adapter

The WCF-BasicHttp send adapter can redeem an SSO ticket from the SSO server to obtain the user credential only in the security configurations shown in the following table.

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
<td><strong>Basic</strong></td>
<td>N/A</td>
</tr>
<tr class="even">
<td><strong>Transport</strong></td>
<td><strong>Digest</strong></td>
<td>N/A</td>
</tr>
<tr class="odd">
<td><strong>TransportCredentialOnly</strong></td>
<td><strong>Basic</strong></td>
<td>N/A</td>
</tr>
<tr class="even">
<td><strong>TransportCredentialOnly</strong></td>
<td><strong>Digest</strong></td>
<td>N/A</td>
</tr>
<tr class="odd">
<td><strong>Message</strong></td>
<td>N/A</td>
<td><strong>UserName</strong></td>
</tr>
<tr class="even">
<td><strong>TransportWithMessageCredential</strong></td>
<td>N/A</td>
<td><strong>UserName</strong></td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-BasicHttp Send Port](https://msdn.microsoft.com/library/bb226467\(v=bts.80\))  
[Installing Certificates for the WCF Adapters](https://msdn.microsoft.com/library/bb245944\(v=bts.80\))  
[Managing BizTalk Hosts and Host Instances](https://msdn.microsoft.com/library/aa561042\(v=bts.80\))  
[How to Change Service Accounts and Passwords](https://msdn.microsoft.com/library/aa561505\(v=bts.80\))

