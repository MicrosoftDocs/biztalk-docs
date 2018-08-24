---
title: <Host Name> Properties Dialog Box, Properties Tab (FTP Adapter Receive Handler)
TOCTitle: <Host Name> Properties Dialog Box, Properties Tab (FTP Adapter Receive Handler)
ms:assetid: ebcad2b8-ae85-47d2-97de-a92bde4013a0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561754(v=BTS.80)
ms:contentKeyID: 51533211
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.ftp.handler.receive.props
---

# \<Host Name\> Properties Dialog Box, Properties Tab (FTP Adapter Receive Handler)

 

Use the **Properties** tab to configure the receive handler for the FTP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Maximum Files</strong></td>
<td>Specify the maximum number of files per BizTalk Server batch.<br />
<br />
Zero (0) indicates no limit.<br />
<br />
 <strong>Default value:</strong> 0</td>
</tr>
<tr class="even">
<td><strong>Maximum Size</strong></td>
<td>Specify the maximum number of bytes per BizTalk Server batch.<br />
<br />
Zero (0) indicates no limit.<br />
<br />
 <strong>Default value:</strong> 0</td>
</tr>
<tr class="odd">
<td><strong>Address</strong></td>
<td>Specify the address of the firewall, either DNS name or IP address.</td>
</tr>
<tr class="even">
<td><strong>Mode</strong></td>
<td>Specify the mode in which the adapter connects to the FTP server.<br />
<br />
 <strong>Valid values:</strong> Passive or Active<br />
<br />
In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br />
<br />
 <strong>Default Value:</strong> Active</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the password for the firewall.</td>
</tr>
<tr class="even">
<td><strong>Port</strong></td>
<td>Specify the port for the firewall.<br />
<br />
 <strong>Valid values:</strong> 1 through 65535 inclusive<br />
<br />
 <strong>Default value:</strong> 21</td>
</tr>
<tr class="odd">
<td><strong>Type</strong></td>
<td>Specify the type of firewall deployed.<br />
<br />
 <strong>Valid values:</strong> Socks 4, Socks 5, None<br />
<br />
 <strong>Default value:</strong> None</td>
</tr>
<tr class="even">
<td><strong>User</strong></td>
<td>Specify the user name for the firewall.</td>
</tr>
<tr class="odd">
<td><strong>Account</strong></td>
<td>Specify the account name for the FTP server.</td>
</tr>
<tr class="even">
<td><strong>After Get</strong></td>
<td>Specify the FTP commands to run after the file GET. Separate commands with a semicolon (;).</td>
</tr>
<tr class="odd">
<td><strong>Before Get</strong></td>
<td>Specify the FTP commands to run before the file GET. Separate commands with a semicolon (;). <strong>Note:</strong> QUIT command is not supported before the file GET.</td>
</tr>
<tr class="even">
<td><strong>Error Threshold</strong></td>
<td>Specify the number of errors that BizTalk Server can encounter before the location is disabled.<br />
<br />
 <strong>Default value:</strong> 10</td>
</tr>
<tr class="odd">
<td><strong>Log</strong></td>
<td>Specify the location to save a copy of the log file. Use this file to diagnose error conditions when sending or receiving files through FTP.</td>
</tr>
<tr class="even">
<td><strong>Max File Size</strong></td>
<td>Specify the maximum downloadable file size, in megabytes (MB).<br />
<br />
Zero (0) indicates no limit.<br />
<br />
 <strong>Default Value:</strong> 100</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the user password to log on to the FTP server.</td>
</tr>
<tr class="even">
<td><strong>Representation</strong></td>
<td>Select how FTP receives the data.<br />
<br />
 <strong>Valid Values:</strong> binary or ASCII<br />
<br />
 <strong>Default Value:</strong> binary</td>
</tr>
<tr class="odd">
<td><strong>User Name</strong></td>
<td>Specify the user name to log on to the FTP server.</td>
</tr>
<tr class="even">
<td><strong>Client Certificate Hash</strong></td>
<td>Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.</td>
</tr>
<tr class="odd">
<td><strong>FTPS Connection Mode</strong></td>
<td>Specify the mode of SSL connection made to the FTPS server.<br />
<br />
 <strong>Valid Values:</strong> Implicit or Explicit<br />
<br />
 <strong>Default Value:</strong> Explicit</td>
</tr>
<tr class="even">
<td><strong>Use Data Protection</strong></td>
<td>Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Specify this as No for the adapter to send and receive data files as plain text.<br />
<br />
This property is applicable only if the <strong>Use SSL</strong> property is set to Yes.<br />
<br />
 <strong>Valid Values:</strong> Yes or No<br />
<br />
 <strong>Default Value:</strong> Yes</td>
</tr>
<tr class="odd">
<td><strong>Use SSL</strong></td>
<td>Specify whether the FTP adapter must use SSL to communicate with the FTPS server. Specify this as Yes only if the FTPS server supports the Transport Layer Security authentication command, AUTH TLS.<br />
<br />
 <strong>Valid Values:</strong> Yes or No<br />
<br />
 <strong>Default Value:</strong> No</td>
</tr>
<tr class="even">
<td><strong>Temporary Folder</strong></td>
<td>Specify the location for a temporary folder. Use this property to guarantee recovery from a transfer failure.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure an FTP Receive Handler](https://msdn.microsoft.com/en-us/library/aa561710\(v=bts.80\))

