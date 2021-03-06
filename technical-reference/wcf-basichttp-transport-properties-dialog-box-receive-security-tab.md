---
description: "Learn more about: WCF-BasicHttp Transport Properties Dialog Box, Receive, Security Tab"
title: WCF-BasicHttp Transport Properties Dialog Box, Receive, Security Tab
TOCTitle: WCF-BasicHttp Transport Properties Dialog Box, Receive, Security Tab
ms:assetid: 648016dc-fe56-4e73-addc-03714d7dc41c
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226322(v=BTS.80)
ms:contentKeyID: 51528515
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-basichttp.transport.receive.security
---

# WCF-BasicHttp Transport Properties Dialog Box, Receive, Security Tab

 

Use the **Security** tab to define the security capabilities of the WCF-BasicHttp receive adapter.

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
- <strong>Transport</strong>: Security is provided using the HTTPS transport. The SOAP messages are secured using HTTPS. To use this mode, you must set up Secure Sockets Layer (SSL) in Microsoft Internet Information Services (IIS).<br />
- <strong>Message</strong>: Security is provided using SOAP message security over the HTTP transport. By default, the SOAP <strong>Body</strong> is encrypted and signed. The only valid <strong>Message client credential type</strong> for the WCF-Basic adapter is <strong>Certificate</strong>. This mode requires the HTTP transport. When using this security mode, the service certificate for this receive location needs to be provided through the <strong>Service certificate - Thumbprint</strong> property.<br />
- <strong>TransportWithMessageCredential</strong>: Integrity, confidentiality, and service authentication are provided by the HTTPS transport. To use this mode, you must set up Secure Sockets Layer (SSL) in Microsoft Internet Information Services (IIS).<br />
- <strong>TransportCredentialOnly</strong>: This mode does not provide message integrity and confidentiality. It provides HTTP-based client authentication. This mode should be used with caution. It should be used in environments where the transport security is provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure. If you select <strong>Certificate</strong> for the <strong>Transport client credential type</strong> property in this security mode, the service certificate for this receive location needs to be provided through the <strong>Service certificate - Thumbprint</strong> property.<br />
<br />
The default is <strong>None</strong>.</td>
</tr>
<tr class="even">
<td><strong>Transport client credential type</strong></td>
<td>Specify the type of credential to be used when performing the client authentication. Valid values include the following:<br />
<br />
- <strong>None</strong>: No authentication occurs at the transport level.<br />
- <strong>Basic</strong>: Basic authentication. In Basic authentication, user names and passwords are sent in plain text over the network. You must create the domain or local user accounts corresponding to the credentials.<br />
- <strong>Digest</strong>: Digest authentication. This authentication method operates much like Basic authentication, except that passwords are sent across the network as a hash value for additional security. Digest authentication is available only on domains with domain controllers running Windows Server operating systems authentication. You must create the domain or local user accounts corresponding to client credentials.<br />
- <strong>Ntlm</strong>: NTLM authentication. Clients can send the credentials without sending a password to this receive location. You must create the domain or local user accounts corresponding to client credentials.<br />
- <strong>Windows</strong>: Windows integrated authentication. Windows Communication Foundation negotiates Kerberos or NTLM, preferring Kerberos if a domain is present. If you want to use Kerberos it is important to have the client identify the service with a service principal name (SPN). You must create the domain or local user accounts corresponding to client credentials.<br />
- <strong>Certificate</strong>: Client authentication using the client certificate. The CA certificate chain for the client X.509 certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the clients can be authenticated to this receive location. <strong>Note:</strong> The <strong>Transport client credential type</strong> property must match the authentication scheme of the IIS virtual directory hosting this receive location. For example, if the property is set to <strong>Windows</strong>, you also need to enable <strong>Integrated Windows authentication</strong> for the virtual directory that hosts it. Similarly if the property is set to <strong>None</strong>, you must allow anonymous access to the virtual directory that hosts this receive location.<br />
<br />
The default is <strong>None</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Message client credential type</strong></td>
<td>Specify the type of credential to be used when performing client authentication using message-based security. Valid values include the following:<br />
<br />
- <strong>UserName</strong>: Allow this receive location to require that clients be authenticated using the <strong>UserName</strong> credential. You must create the domain or local user accounts corresponding to the client credentials.<br />
- <strong>Certificate</strong>: Clients are authenticated to this receive location using the client certificate. The CA certificate chain for the client X.509 certificates must be installed in the Trusted Root Certification Authorities certificate store of this computer so that the clients can be authenticated to this receive location.<br />
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
<td><strong>Service certificate -Thumbprint</strong></td>
<td>Specify the thumbprint of the X.509 certificate for this receive location that the clients use to authenticate the service. The thumbprint can be selected by navigating the <strong>My</strong> store in the <strong>Current User</strong> location with the <strong>Browse</strong> button. <strong>Note:</strong> You must install the service certificate into the <strong>Current User</strong> location of the user account for the receive handler hosting this receive location.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 40<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Use Single Sign-On</strong></td>
<td>Use Single Sign-On to retrieve client credentials to issue an SSO ticket. This option is valid only for the security configurations listed in the following section, &quot;Enterprise Single Sign-On Supportability for the WCF-BasicHttp Receive Adapter.&quot;<br />
<br />
The default value is cleared.</td>
</tr>
</tbody>
</table>


## Enterprise Single Sign-On Supportability for the WCF-BasicHttp Receive Adapter

The WCF-BasicHttp receive adapter can issue an SSO ticket from the SSO server only in the security configurations shown in the following table.

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
<td><strong>Transport</strong></td>
<td><strong>Ntlm</strong></td>
<td>N/A</td>
</tr>
<tr class="even">
<td><strong>Transport</strong></td>
<td><strong>Windows</strong></td>
<td>N/A</td>
</tr>
<tr class="odd">
<td><strong>Transport</strong></td>
<td><strong>Certificate</strong></td>
<td>N/A</td>
</tr>
<tr class="even">
<td><strong>Message</strong></td>
<td>N/A</td>
<td><strong>UserName</strong></td>
</tr>
<tr class="odd">
<td><strong>TransportWithMessageCredential</strong></td>
<td>N/A</td>
<td><strong>UserName</strong></td>
</tr>
<tr class="even">
<td><strong>TransportCredentialOnly</strong></td>
<td><strong>Basic</strong></td>
<td>N/A</td>
</tr>
<tr class="odd">
<td><strong>TransportCredentialOnly</strong></td>
<td><strong>Digest</strong></td>
<td>N/A</td>
</tr>
<tr class="even">
<td><strong>TransportCredentialOnly</strong></td>
<td><strong>Ntlm</strong></td>
<td>N/A</td>
</tr>
<tr class="odd">
<td><strong>TransportCredentialOnly</strong></td>
<td><strong>Windows</strong></td>
<td>N/A</td>
</tr>
<tr class="even">
<td><strong>TransportCredentialOnly</strong></td>
<td><strong>Certificate</strong></td>
<td>N/A</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-BasicHttp Receive Location](https://msdn.microsoft.com/library/bb246064\(v=bts.80\))  
[Installing Certificates for the WCF Adapters](https://msdn.microsoft.com/library/bb245944\(v=bts.80\))  
[Configuring IIS for the Isolated WCF Receive Adapters](https://msdn.microsoft.com/library/bb245982\(v=bts.80\))  
[Managing BizTalk Hosts and Host Instances](https://msdn.microsoft.com/library/aa561042\(v=bts.80\))  
[How to Change Service Accounts and Passwords](https://msdn.microsoft.com/library/aa561505\(v=bts.80\))

