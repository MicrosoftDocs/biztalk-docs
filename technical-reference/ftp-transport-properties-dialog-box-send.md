---
title: FTP Transport Properties Dialog Box, Send
TOCTitle: FTP Transport Properties Dialog Box, Send
ms:assetid: 0cdcb574-2574-4d56-be60-8c7d2e14e425
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547313(v=BTS.80)
ms:contentKeyID: 51526190
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.ftp.transport.props2
---

# FTP Transport Properties Dialog Box, Send

 

Use the **FTP Transport Properties** dialog box to configure the send port for the FTP adapter.


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
<td><strong>Address</strong></td>
<td>Specify the address of the firewall, either a DNS name or an IP address.</td>
</tr>
<tr class="even">
<td><strong>Mode</strong></td>
<td>Specify the mode in which the adapter connects to the FTP server.<br />
<br />
 <strong>Valid values:</strong> Passive and Active<br />
<br />
In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br />
<br />
 <strong>Default value:</strong> Active</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the password for the firewall.</td>
</tr>
<tr class="even">
<td><strong>Port</strong></td>
<td>Specify the port for the firewall.<br />
<br />
 <strong>Valid values:</strong> From 1 through 65,535<br />
<br />
 <strong>Default value:</strong> 21</td>
</tr>
<tr class="odd">
<td><strong>Type</strong></td>
<td>Specify the type of firewall deployed.<br />
<br />
 <strong>Valid values:</strong> None, Socks 4, and Socks 5<br />
<br />
 <strong>Default value:</strong> None</td>
</tr>
<tr class="even">
<td><strong>User</strong></td>
<td>Specify the user name for the firewall.</td>
</tr>
<tr class="odd">
<td><strong>Account</strong></td>
<td>Optional. Specify the account name for the FTP server. This option is deprecated in BizTalk Server and use of this property is discouraged.</td>
</tr>
<tr class="even">
<td><strong>After Put</strong></td>
<td>Specify the FTP commands to run after the file <strong>PUT</strong>. Separate commands with a semi-colon (;).</td>
</tr>
<tr class="odd">
<td><strong>Allocate Storage</strong></td>
<td>Specify whether to allocate storage space for legacy host systems. This option is provided for backward compatibility but is not used by BizTalk Server.<br />
<br />
 <strong>Valid values:</strong> No, and Yes<br />
<br />
 <strong>Default value:</strong> No</td>
</tr>
<tr class="even">
<td><strong>Before Put</strong></td>
<td>Specify the FTP commands to run before the file <strong>PUT</strong>, such as commands to change default values on the FTP server. Separate commands with a semicolon (;). No open command is required. <strong>Note:</strong> QUIT command is not supported before the file PUT.</td>
</tr>
<tr class="odd">
<td><strong>Folder</strong></td>
<td>Specify the location to move the files to on the FTP server.</td>
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
<td><strong>Port</strong></td>
<td>Specify the port address for this FTP server.<br />
<br />
 <strong>Default value:</strong> 21</td>
</tr>
<tr class="odd">
<td><strong>Representation</strong></td>
<td>Select how FTP sends the data, either binary or ASCII.<br />
<br />
 <strong>Valid values:</strong> binary or ASCII<br />
<br />
 <strong>Default value:</strong> binary</td>
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
<td><strong>Target File Name</strong></td>
<td>Specify an alternative name for the file. Retaining the default name will guarantee unique message names for each message sent.<br />
<br />
 <strong>Default value:</strong> %MessageID%.xml</td>
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
 <strong>Valid values:</strong> Implicit or Explicit<br />
<br />
 <strong>Default value:</strong> Explicit</td>
</tr>
<tr class="even">
<td><strong>Use Data Protection</strong></td>
<td>Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Specify this as No for the adapter to send and receive data files as plain text.<br />
<br />
This property is applicable only if the <strong>Use SSL</strong> property is set to Yes.<br />
<br />
 <strong>Valid values:</strong> Yes or No<br />
<br />
 <strong>Default value:</strong> Yes</td>
</tr>
<tr class="odd">
<td><strong>Use SSL</strong></td>
<td>Specify whether the FTP adapter must use SSL to communicate with the FTPS server. Specify this as Yes only if the FTPS server supports the Transport Layer Security authentication command, AUTH TLS.<br />
<br />
 <strong>Valid values:</strong> Yes or No<br />
<br />
 <strong>Default value:</strong> No</td>
</tr>
<tr class="even">
<td><strong>Connection Limit</strong></td>
<td>Specify the maximum number of concurrent FTP connections that can be opened to the server. A value of 0 means no limit.<br />
<br />
 <strong>Default value:</strong> 0 <strong>Note:</strong> This property replaces the registry entry that was used in earlier versions of BizTalk Server to govern the connection limit. The registry entry used to control the Connection Limit is ignored by BizTalk Server.</td>
</tr>
<tr class="odd">
<td><strong>Temporary Folder</strong></td>
<td>Specify the location for a temporary folder on the FTP server. If a binary file is uploaded, this folder is used to guarantee recovery from a transfer failure.<br />
<br />
If an ASCII file is uploaded, the file is first uploaded here and then moved to the destination FTP folder. In the event of transfer failure, the adapter restarts the upload.<br />
<br />
Use of this property supports atomic writing of files.</td>
</tr>
</tbody>
</table>


## See Also

[Restrictions on Using Macros in File Names](https://msdn.microsoft.com/library/aa578022\(v=bts.80\))  
[How to Configure an FTP Send Port](https://msdn.microsoft.com/library/aa546802\(v=bts.80\))  
[Enhancements to the FTP Adapter](https://msdn.microsoft.com/library/ff629768\(v=bts.80\))

