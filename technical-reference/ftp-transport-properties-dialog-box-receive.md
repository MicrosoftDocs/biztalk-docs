---
description: "Learn more about: FTP Transport Properties Dialog Box, Receive"
title: FTP Transport Properties Dialog Box, Receive
TOCTitle: FTP Transport Properties Dialog Box, Receive
ms:assetid: c1eb4f71-3fe9-4c49-9a42-6d7a9858f244
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547828(v=BTS.80)
ms:contentKeyID: 51530956
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.ftp.transport.props1
---

# FTP Transport Properties Dialog Box, Receive

 

Use the **FTP Transport Properties** dialog box to configure the receive location for the FTP adapter.


> [!NOTE]
> <P>You can resize the description pane at the bottom of the dialog box by dragging the double-headed arrow that appears on the top border of the pane.</P>



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
Default value: 0</td>
</tr>
<tr class="even">
<td><strong>Maximum Size</strong></td>
<td>Specify the maximum number of bytes per BizTalk Server batch.<br />
<br />
Zero (0) indicates no limit.<br />
<br />
Default value: 0</td>
</tr>
<tr class="odd">
<td><strong>Address</strong></td>
<td>Specify the address of the firewall, either a DNS name or an IP address.</td>
</tr>
<tr class="even">
<td><strong>Mode</strong></td>
<td>Specify the mode in which the adapter connects to the FTP server.<br />
<br />
Valid values: Passive and Active<br />
<br />
In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br />
<br />
Default value: Active</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the password for the firewall.</td>
</tr>
<tr class="even">
<td><strong>Port</strong></td>
<td>Specify the port for the firewall.<br />
<br />
Valid values: From 1 through 65,535<br />
<br />
Default value: 21</td>
</tr>
<tr class="odd">
<td><strong>Type</strong></td>
<td>Specify the type of firewall deployed.<br />
<br />
Valid values: None, Socks 4, and Socks 5<br />
<br />
Default value: None</td>
</tr>
<tr class="even">
<td><strong>User</strong></td>
<td>Specify the user name for the firewall.</td>
</tr>
<tr class="odd">
<td><strong>Account</strong></td>
<td>Specify the account name for the FTP server.<br />
<br />
This property is optional.</td>
</tr>
<tr class="even">
<td><strong>After Get</strong></td>
<td>Specify the FTP commands to run after the file GET. Separate commands with a semi-colon (;).</td>
</tr>
<tr class="odd">
<td><strong>Before Get</strong></td>
<td>Specify the FTP commands to run before the file GET. Separate commands with a semi-colon (;). <strong>Note:</strong> QUIT command is not supported before the file GET.</td>
</tr>
<tr class="even">
<td><strong>Error Threshold</strong></td>
<td>Specify the number of errors that BizTalk Server can encounter before the location is disabled.<br />
<br />
Default value: 10</td>
</tr>
<tr class="odd">
<td><strong>File Mask</strong></td>
<td>Specify the file mask filter to use when transmitting files.</td>
</tr>
<tr class="even">
<td><strong>Folder</strong></td>
<td>Specify the polling location on the FTP server.</td>
</tr>
<tr class="odd">
<td><strong>Log</strong></td>
<td>Specify the location to save a copy of a log file. You use this file to diagnose error conditions when you send or receive files through FTP.</td>
</tr>
<tr class="even">
<td><strong>Max File Size</strong></td>
<td>Specify the maximum downloadable file size, in megabytes.<br />
<br />
Zero (0) indicates no limit on the file size.<br />
<br />
Default value: 100</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the user password to log on to the FTP server.</td>
</tr>
<tr class="even">
<td><strong>Port</strong></td>
<td>Specify the port address for this FTP server.<br />
<br />
Default value: 21</td>
</tr>
<tr class="odd">
<td><strong>Representation</strong></td>
<td>Select how FTP receives the data.<br />
<br />
Valid values: binary or ASCII<br />
<br />
Default value: binary</td>
</tr>
<tr class="even">
<td><strong>Server</strong></td>
<td>Specify the server name or IP address of the FTP server.</td>
</tr>
<tr class="odd">
<td><strong>SSO Affiliate</strong></td>
<td>Specify the Single Sign-On affiliate application.</td>
</tr>
<tr class="even">
<td><strong>Use name list (NLST)</strong></td>
<td>Specify how the adapter lists files. To view file names instead of the system-defined file listing, set this value to Yes.<br />
<br />
Default value: No</td>
</tr>
<tr class="odd">
<td><strong>User Name</strong></td>
<td>Specify the user name to log on to the FTP server.</td>
</tr>
<tr class="even">
<td><strong>Delete After Download</strong></td>
<td>Specify whether the adapter deletes a file from the FTP server after downloading it.<br />
<br />
Default value: Yes<br />
<br />
If the adapter does not have permissions to delete a file from the FTP server, set the <strong>Enable Timestamp Comparison</strong> property.</td>
</tr>
<tr class="odd">
<td><strong>Enable Timestamp Comparison</strong></td>
<td>Specify whether the adapter downloads a file again based on its modified timestamp. Set this value to Yes when the adapter does not have sufficient permissions to delete a file from the FTP server.<br />
<br />
Default value: No<br />
<br />
Set this value to Yes only if the FTP server supports the command MDTM. If the FTP server does not support MDTM, set the <strong>Redownload Interval</strong> property.</td>
</tr>
<tr class="even">
<td><strong>Interval</strong></td>
<td>Specify the interval number for polling this location. To continuously poll, set this value to zero (0).<br />
<br />
Default value: 60</td>
</tr>
<tr class="odd">
<td><strong>Redownload Interval</strong></td>
<td>Specify the interval at the lapse of which the adapter downloads files again. This property is useful when the FTP server does not allow for comparison of the file’s modified timestamp.<br />
<br />
Default value: -1<br />
<br />
-1 indicates that the adapter will not download the file again.<br />
<br />
0 indicates that the adapter will download the file in each polling cycle.</td>
</tr>
<tr class="even">
<td><strong>Unit</strong></td>
<td>Specify the type of units for the Interval and Redownload Interval properties.<br />
<br />
Valid values: Seconds, Minutes, Hours, and Days<br />
<br />
Default value: Seconds</td>
</tr>
<tr class="odd">
<td><strong>Client Certificate Hash</strong></td>
<td>Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.</td>
</tr>
<tr class="even">
<td><strong>FTPS Connection Mode</strong></td>
<td>Specify the mode of SSL connection made to the FTPS server.<br />
<br />
 <strong>Valid values:</strong> Implicit or Explicit<br />
<br />
 <strong>Default value:</strong> Explicit</td>
</tr>
<tr class="odd">
<td><strong>Use Data Protection</strong></td>
<td>Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Specify this as No for the adapter to send and receive data files as plaintext.<br />
<br />
This property is applicable only if the <strong>Use SSL</strong> property is set to Yes.<br />
<br />
 <strong>Valid values:</strong> Yes or No<br />
<br />
 <strong>Default value:</strong> Yes</td>
</tr>
<tr class="even">
<td><strong>Use SSL</strong></td>
<td>Specify whether the FTP adapter must use SSL to communicate with the FTPS server. Specify this as Yes only if the FTPS server supports the Transport Layer Security authentication command, AUTH TLS.<br />
<br />
 <strong>Valid values:</strong> Yes or No<br />
<br />
 <strong>Default value:</strong> No</td>
</tr>
<tr class="odd">
<td><strong>Receive Data Timeout</strong></td>
<td>Specify the time in milliseconds before the receive call will abort. You use this to prevent a slow server from causing the receive location to stop responding.<br />
<br />
 <strong>Default value:</strong> 90000</td>
</tr>
<tr class="even">
<td><strong>Temporary Folder</strong></td>
<td>Specify the location for a temporary folder. You use this location to guarantee recovery from a transfer failure.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure an FTP Receive Location](https://msdn.microsoft.com/library/aa559095\(v=bts.80\))

