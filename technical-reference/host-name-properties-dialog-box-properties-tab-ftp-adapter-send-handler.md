---
title: <Host Name> Properties Dialog Box, Properties Tab (FTP Adapter Send Handler)
TOCTitle: <Host Name> Properties Dialog Box, Properties Tab (FTP Adapter Send Handler)
ms:assetid: c289993c-3bb8-4755-b4d7-5504c5e10a7c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547840(v=BTS.80)
ms:contentKeyID: 51530967
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.ftp.handler.send.props
---

# \<Host Name\> Properties Dialog Box, Properties Tab (FTP Adapter Send Handler)

 

Use the **Properties** tab to configure the send handler for the FTP adapter.

<table>
<thead>
<tr class="header">
<th><strong>Use this</strong></th>
<th><strong>To do this</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Maximum Files</strong></td>
<td>Specify the maximum number of files per BizTalk Server batch.<br />
<br />
Valid values: from 1 through 200<br />
<br />
Default value: 50</td>
</tr>
<tr class="even">
<td><strong>Address</strong></td>
<td>Specify the address of the firewall, either a DNS name or an IP address.</td>
</tr>
<tr class="odd">
<td><strong>Mode</strong></td>
<td>Specify the mode in which the adapter connects to the FTP server.<br />
<br />
Valid values: Passive and Active<br />
<br />
In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br />
<br />
Default value: Active</td>
</tr>
<tr class="even">
<td><strong>Password</strong></td>
<td>Specify the password for the firewall.</td>
</tr>
<tr class="odd">
<td><strong>Port</strong></td>
<td>Specify the port for the firewall.<br />
<br />
Valid values: from 1 through 65535<br />
<br />
Default values:21</td>
</tr>
<tr class="even">
<td><strong>Type</strong></td>
<td>Specify the type of firewall deployed.<br />
<br />
Valid values: Socks 4, Socks 5, None<br />
<br />
Default value: None</td>
</tr>
<tr class="odd">
<td><strong>User</strong></td>
<td>Specify the user name for the firewall.</td>
</tr>
<tr class="even">
<td><strong>Account</strong></td>
<td>Optional. Specify the account name for the FTP server.</td>
</tr>
<tr class="odd">
<td><strong>After Put</strong></td>
<td>Specify the FTP command to run after the file PUT. Separate commands with a semicolon (;).</td>
</tr>
<tr class="even">
<td><strong>Allocate Storage</strong></td>
<td>Specify the use for allocating storage space for some legacy host systems.<br />
<br />
Valid values: Yes and No<br />
<br />
Default value: No</td>
</tr>
<tr class="odd">
<td><strong>Before Put</strong></td>
<td>Specify the FTP commands to run before the file PUT, such as commands to change default values on the FTP server. Separate commands with a semicolon (;). No open command is required. <strong>Note:</strong> QUIT command is not supported before the file PUT.</td>
</tr>
<tr class="even">
<td><strong>Log</strong></td>
<td>Specify the location to save a copy of a log file. Use this file to diagnose error conditions when you send or receive files through FTP.</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the user password to log on to the FTP server.</td>
</tr>
<tr class="even">
<td><strong>Representation</strong></td>
<td>Select how FTP sends the data, either binary or ASCII.<br />
<br />
Valid values: binary and ASCII<br />
<br />
Default value: binary</td>
</tr>
<tr class="odd">
<td><strong>Target File Name</strong></td>
<td>Specify the pattern for the destination file name.<br />
<br />
Default value: %MessageID%.xml</td>
</tr>
<tr class="even">
<td><strong>User Name</strong></td>
<td>Specify the user name to log on to the FTP server.</td>
</tr>
<tr class="odd">
<td><strong>Client Certificate Hash</strong></td>
<td>Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.</td>
</tr>
<tr class="even">
<td><strong>FTPS Connection Mode</strong></td>
<td>Specify the mode of SSL connection made to the FTPS server.<br />
<br />
Valid values: Implicit or Explicit<br />
<br />
Default value: Explicit</td>
</tr>
<tr class="odd">
<td><strong>Use Data Protection</strong></td>
<td>Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server.<br />
<br />
This property is applicable only if the <strong>Use SSL</strong> property is set to Yes.<br />
<br />
Valid values: Yes or No<br />
<br />
Default value: Yes</td>
</tr>
<tr class="even">
<td><strong>Use SSL</strong></td>
<td>Specify whether the FTP adapter must use SSL to communicate with the FTPS server. Specify this as Yes only if the FTPS server supports the Transport Layer Security authentication command, AUTH TLS.<br />
<br />
Valid values: Yes or No<br />
<br />
Default value: No</td>
</tr>
<tr class="odd">
<td><strong>Temporary Folder</strong></td>
<td>Specify the location for a temporary folder on the FTP server. If a binary file is uploaded, this folder is used to guarantee recovery from a transfer failure.<br />
<br />
If an ASCII file is uploaded, the file is first uploaded to this folder and then moved to the destination FTP folder. In the event of transfer failure, the adapter restarts upload. <strong>Note:</strong> Use of this property supports atomic writing of files.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure an FTP Send Handler](https://msdn.microsoft.com/library/aa561311\(v=bts.80\))  
[Enhancements to the FTP Adapter](https://msdn.microsoft.com/library/ff629768\(v=bts.80\))

