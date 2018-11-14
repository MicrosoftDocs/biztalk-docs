---
title: Configuration Wizard, Enterprise Single Sign-On Page
TOCTitle: Configuration Wizard, Enterprise Single Sign-On Page
ms:assetid: 15c013f1-a7ff-4c56-a6e6-babf3c3d38ae
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa558719(v=BTS.80)
ms:contentKeyID: 51526399
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.config.wizard.sso
---

# Configuration Wizard, Enterprise Single Sign-On Page

 

Use the **Enterprise Single Sign-On (SSO)** page to configure SSO settings for your BizTalk Server environment.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Enable Enterprise Single Sign-On on this computer</strong></td>
<td>Select <strong>Enable Enterprise Single Sign-On on this computer</strong> to configure this server with SSO settings.</td>
</tr>
<tr class="even">
<td><strong>Create a new SSO system</strong></td>
<td>Select <strong>Create a new SSO system</strong> if this is the first SSO server you configure in your SSO system. This will also create and configure the SSO database. You must also back up the secret on this secret server. <strong>Important:</strong> You should configure the master secret server as a stand-alone server. You must be an SSO administrator while performing this configuration task.</td>
</tr>
<tr class="odd">
<td><strong>Join an existing SSO system</strong></td>
<td>Select <strong>Join an existing SSO system</strong> to connect to an existing SSO system in the BizTalk Server environment.</td>
</tr>
<tr class="even">
<td><strong>Data stores</strong></td>
<td>The Data stores list provides an editable view of the data stores used for the SSO database.</td>
</tr>
<tr class="odd">
<td><strong>Windows service</strong></td>
<td>The Windows service list provides an editable view of the account used to run the Enterprise Single Sign-On service.</td>
</tr>
<tr class="even">
<td><strong>Windows accounts</strong></td>
<td>The Windows accounts list provides an editable view of the SSO Administrators and SSO Affiliate Administrators Windows groups.</td>
</tr>
</tbody>
</table>


Use the **Enterprise Single Sign-On Secret Backup** page to save the master secret to an encrypted backup file in case of system recovery.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Secret backup password</strong></td>
<td>Type the password for the backup file.</td>
</tr>
<tr class="even">
<td><strong>Confirm secret backup password</strong></td>
<td>Confirm the password for the backup file.</td>
</tr>
<tr class="odd">
<td><strong>Secret backup reminder</strong></td>
<td>Type a reminder for the password you enter.</td>
</tr>
<tr class="even">
<td><strong>Secret backup file</strong></td>
<td>Provide a file name and file path to the secret backup file. By default it is stored at \Program Files\Common Files\Enterprise Single Sign-On\.</td>
</tr>
</tbody>
</table>


## See Also

[Installation Overview for BizTalk Server 2013 and 2013 R2](https://msdn.microsoft.com/library/jj248688\(v=bts.80\))  
[Getting Started](https://msdn.microsoft.com/library/aa560946\(v=bts.80\))

