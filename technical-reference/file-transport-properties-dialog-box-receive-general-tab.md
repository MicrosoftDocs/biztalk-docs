---
title: File Transport Properties Dialog Box, Receive, General Tab
TOCTitle: File Transport Properties Dialog Box, Receive, General Tab
ms:assetid: cd3061d7-9ef7-4a26-8809-fe394f97f064
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa548062(v=BTS.80)
ms:contentKeyID: 51531400
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.file.transport.receive.general
---

# File Transport Properties Dialog Box, Receive, General Tab

 

Use the **General** tab to configure the receive location for the File adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Receive folder</strong></td>
<td>Required. Specify the path to a folder on the file system or network share from where the file receive handler reads files. The path can be entered directly into the Receive folder text box or can be selected from the file system by navigating to the folder with the Browse button. When browsing for the folder in the Browse For Folder dialog box you also have the option to create a new folder by clicking the Make New Folder button.<br />
<br />
Type: String <strong>Note:</strong> Do not set the Receive folder property to a folder that uses the NT Distributed File System with a symbolic link. If you are using an NT Distributed File System, you can only use folders with straight network paths in File Adapter Receive Locations.</td>
</tr>
<tr class="even">
<td><strong>File mask</strong></td>
<td>Required. Specify the mask for the files. This mask can contain the standard wildcard value (*).<br />
<br />
Default value: *.xml<br />
<br />
Type: String</td>
</tr>
<tr class="odd">
<td><strong>Public address</strong></td>
<td>Specify the public address of this location. This address is exposed to external partners.<br />
<br />
If this property is not specified, then the run-time engine replaces it as:<br />
<br />
file://&lt;Receive folder&gt;/&lt;File mask&gt;<br />
<br />
The value for this property requires an adapter prefix.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>Retry count</strong></td>
<td>Specify the number of attempts to access the receive location on a network share if it is temporarily unavailable.<br />
<br />
Default Value: 5<br />
<br />
Type: Long<br />
<br />
Minimum value: 0<br />
<br />
Maximum value: MAX_LONG</td>
</tr>
<tr class="odd">
<td><strong>Retry interval (min)</strong></td>
<td>Specify the retry interval time (in minutes) between attempts to access the receive location on the network share if it is temporarily unavailable.<br />
<br />
Default Value: 5 minutes<br />
<br />
Type: Long<br />
<br />
Minimum value: 0<br />
<br />
Maximum value: MAX_LONG</td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a File Receive Location](https://msdn.microsoft.com/library/aa547108\(v=bts.80\))  
[Restrictions on the File Mask and File Name Properties](https://msdn.microsoft.com/library/aa578688\(v=bts.80\))

