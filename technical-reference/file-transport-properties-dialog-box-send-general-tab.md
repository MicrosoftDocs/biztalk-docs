---
description: "Learn more about: File Transport Properties Dialog Box, Send, General Tab"
title: File Transport Properties Dialog Box, Send, General Tab
TOCTitle: File Transport Properties Dialog Box, Send, General Tab
ms:assetid: d8f5d4f7-97c0-4ff9-b4b6-13ceb2fe6f83
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578689(v=BTS.80)
ms:contentKeyID: 51531733
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.file.transport.send.general
ms.topic: ui-reference
---

# File Transport Properties Dialog Box, Send, General Tab

 

Use the **General** tab to configure the send port for the File adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Destination folder</strong></td>
<td>Specify the path to the location on the file system or public share to write the output messages. The path can be entered directly into the Destination Location text box or can be selected from the file system by navigating to the folder with the Browse button. When browsing for the folder in the Browse For Folder dialog box you also have the option to create a new folder by clicking the Make New Folder button.</td>
</tr>
<tr class="even">
<td><strong>File name</strong></td>
<td>Specify the name of the file where the file send handler writes the message.</td>
</tr>
<tr class="odd">
<td><strong>Copy mode</strong></td>
<td>Define the copy mode to use when writing a message to a file. Valid values are:<br />
<br />
Append: The file send handler opens a file if it exists and appends a message to the end of the file. If the file does not exist, the file send handler creates a new file.<br />
<br />
Overwrite: The file send handler opens a file if it exists and overwrites its content. If the file does not exist, the file send handler creates a new file.<br />
<br />
Create new: If the file does not exist, the file send handler creates a file and writes to it. If the file already exists, the file send handler reports an error and then follows common adapter retry logic for send ports. This is a default copy mode for the file send handler.</td>
</tr>
<tr class="even">
<td><strong>Allow cache on write</strong></td>
<td>Define whether to use file system caching when writing a message to a file.<br />
<br />
Options:<br />
<br />
False. Do not use the file system cache.<br />
<br />
True. Use the file system cache. <strong>Important:</strong> Setting this property to True can increase the performance of the file adapter at the risk of potential data loss when there is a loss of power and not all data is written to disk.</td>
</tr>
<tr class="odd">
<td><strong>Use temporary file while writing</strong></td>
<td>Defines whether to write the output file to a temporary file first and then rename the file once the write operation has completed. If this option is enabled then the temporary file will be created with the extension <strong>BTS-WIP</strong>.<br />
<br />
Valid values are:<br />
<br />
 <strong>True (checked)</strong> The File adapter creates a temporary file when writing to the target folder.<br />
<br />
 <strong>False (not checked)</strong> The File adapter does not create a temporary file when writing to the target folder. <strong>Note:</strong> This option is only available when the <strong>CopyMode</strong> property is set to a value of <strong>Create new</strong>.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a File Receive Location](https://msdn.microsoft.com/library/aa547108\(v=bts.80\))  
[Restrictions on the File Mask and File Name Properties](https://msdn.microsoft.com/library/aa578688\(v=bts.80\))  
[Restrictions on Using Macros in File Names](https://msdn.microsoft.com/library/aa578022\(v=bts.80\))

