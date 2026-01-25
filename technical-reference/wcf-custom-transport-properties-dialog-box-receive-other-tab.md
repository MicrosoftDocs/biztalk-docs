---
description: "Learn more about: WCF-Custom Transport Properties Dialog Box, Receive, Other Tab"
title: WCF-Custom Transport Properties Dialog Box, Receive, Other Tab
TOCTitle: WCF-Custom Transport Properties Dialog Box, Receive, Other Tab
ms:assetid: f28cf430-400a-4ce0-8378-f2c0f98b41f4
ms:mtpsurl: https://msdn.microsoft.com/library/Bb259968(v=BTS.80)
ms:contentKeyID: 51533392
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.transport.receive.other
---

# WCF-Custom Transport Properties Dialog Box, Receive, Other Tab

 

Use the **Other** tab to specify the following:

  - The credentials for this receive location to use when polling an external service

  - Whether this receive location issues an SSO ticket

  - Whether this receive location preserves message order when processing messages

You can create a custom channel to poll an external service to retrieve response messages from the service like the SQL receive adapter and the FTP receive adapter do. If you configure the custom binding to use this custom channel, the receive location uses the specified credentials when sending solicit messages to an external service.


> [!NOTE]
> <P>For this receive location to use the credentials specified on the <STRONG>Other</STRONG> tab, you must use the <STRONG>ClientCredentials</STRONG> object that BizTalk Server passes along when implementing the custom channel and binding.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Credentials - None</strong></td>
<td>Do not use any credentials when this receive location sends solicit messages to poll an external service, or this receive location does not need to poll any external service.<br />
<br />
This is the default setting.</td>
</tr>
<tr class="even">
<td><strong>Credentials - User account</strong></td>
<td>Use the credentials specified in the <strong>Username</strong> and <strong>Password</strong> properties when this receive location sends solicit messages to poll an external service.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Credentials - User name</strong></td>
<td>Specify the user name for this receive location to use when polling an external service to retrieve response messages. This property is required when the <strong>User account</strong> option is selected.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Credentials - Password</strong></td>
<td>Specify the password for this receive location to use when polling an external service to retrieve response messages. This property is required when the <strong>User account</strong> option is selected.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Credentials - Get credentials from affiliate application</strong></td>
<td>Use the SSO affiliate application specified in the <strong>Affiliate application</strong> property when this receive location sends solicit messages to poll an external service.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Credentials - Affiliate application</strong></td>
<td>Specify the SSO affiliate application to return external credentials to be used when this receive location sends solicit messages to poll an external service. The specified SSO affiliate application must have a mapping between the Windows account under which this receive location runs and the account for the external service. This property is required when the <strong>Get credentials from affiliate application</strong> option is selected.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Credentials - Issue Single Sign-On ticket</strong></td>
<td>Use Single Sign-On to retrieve client credentials to issue an SSO ticket. This option requires using the security mode that allows this receive location to impersonate the user account to issue an SSO ticket.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Message order - Ordered processing</strong></td>
<td>Preserve message order when processing messages (for use with the NetMsmq binding).<br />
<br />
The default value is cleared.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-Custom Receive Location](https://msdn.microsoft.com/library/bb259941\(v=bts.80\))  
[How to Configure a WCF-CustomIsolated Receive Location](https://msdn.microsoft.com/library/bb226374\(v=bts.80\))

