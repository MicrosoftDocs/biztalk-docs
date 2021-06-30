---
description: "Learn more about: Host Properties Dialog Box"
title: Host Properties Dialog Box
TOCTitle: Host Properties Dialog Box
ms:assetid: 2241f922-3a90-429e-91cb-72f972dee70b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559181(v=BTS.80)
ms:contentKeyID: 51526788
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.host.properties
---

# Host Properties Dialog Box

Use the **Host Properties** window to view the common properties of the selected send handler.

## General Tab

The following table lists the UIElements in the **General** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Name</strong></td>
<td>Displays the name of the host. You name the host when you create it.</td>
</tr>
<tr class="even">
<td><strong>Type</strong></td>
<td>Displays the host type. You can enlist an orchestration to an In-process host, and an In-process host can host a send handler. An Isolated host operates outside the BizTalk Server installation.</td>
</tr>
<tr class="odd">
<td><strong>Options - Allow Host Tracking</strong></td>
<td>Select this check box to indicate that the host loads the BizTalk Tracking component to process health monitoring and business data. If you select this check box, the current host will have read/write privileges to the tracking tables in the MessageBox database, as well as to the Tracking database. Accordingly, any objects running in this host will also have read/write access privileges to these databases. If you clear the check box, the host will have only write access to the tracking tables in the MessageBox database and will not have access to the Tracking database.</td>
</tr>
<tr class="even">
<td><strong>Options - Authentication Trusted</strong></td>
<td>Select this check box to specify that BizTalk should trust this host.</td>
</tr>
<tr class="odd">
<td><strong>Options - 32-bit only</strong></td>
<td>Select this check box if you want the host instance process to be created as 32-bit on both 32-bit and 64-bit servers. If this check box is cleared, the host instance process will be created as 32-bit on 32-bit servers and as 64-bit on 64-bit servers.</td>
</tr>
<tr class="even">
<td><strong>Options - Make this the default host in the group</strong></td>
<td>Select this check box to identify this host as the default host. The orchestration enlistment process automatically uses the default host to host the orchestration, unless you explicitly select a different host. If this check box is selected and unavailable, this host is the default.</td>
</tr>
<tr class="odd">
<td><strong>Windows group</strong></td>
<td>Type the local or domain group for the host. Members of the Windows group will have permissions to run instances of this host.</td>
</tr>
</tbody>
</table>

## Certificates Tab

The following table lists the UIElements in the **Certificates** tab and what they are used for.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Decryption certificate - Common Name</strong></td>
<td>Displays the common name of the displayed decryption certificate.</td>
</tr>
<tr class="even">
<td><strong>Decryption certificate - Thumbprint</strong></td>
<td>Displays the thumbprint of the private key certificate used to decrypt inbound messages for this host. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number 0 to 9 or a letter A to F).</td>
</tr>
<tr class="odd">
<td><strong>Decryption certificate - Remove certificate</strong></td>
<td>Click to remove the displayed decryption certificate from the host.</td>
</tr>
<tr class="even">
<td><strong>Decryption certificate - Browse</strong></td>
<td>Click to display the <strong>Select Certificate</strong> dialog box, where you select the decryption certificate from the Personal store that you want to use with the host.</td>
</tr>
</tbody>
</table>

## See Also

[Hosts](https://msdn.microsoft.com/library/aa578695\(v=bts.80\))  
[Host Groups](https://msdn.microsoft.com/library/aa547356\(v=bts.80\))  
[Host Instances](https://msdn.microsoft.com/library/aa560673\(v=bts.80\))  
[How to Create a New Host](https://msdn.microsoft.com/library/aa561079\(v=bts.80\))  
[How to Delete a Host](https://msdn.microsoft.com/library/aa561590\(v=bts.80\))  
[Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\))
