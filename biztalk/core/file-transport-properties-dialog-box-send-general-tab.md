---
title: "File Transport Properties Dialog Box, Send, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.file.transport.send.general"
helpviewer_keywords: 
  - "file transport, properties"
  - "file transport, configuring"
  - "configuring, file transport"
ms.assetid: d8f5d4f7-97c0-4ff9-b4b6-13ceb2fe6f83
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Transport Properties Dialog Box, Send, General Tab
Use the **General** tab to configure the send port for the File adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Destination folder**|Specify the path to the location on the file system or public share to write the output messages. The path can be entered directly into the Destination Location text box or can be selected from the file system by navigating to the folder with the Browse button. When browsing for the folder in the Browse For Folder dialog box you also have the option to create a new folder by clicking the Make New Folder button.|  
|**File name**|Specify the name of the file where the file send handler writes the message.|  
|**Copy mode**|Define the copy mode to use when writing a message to a file. Valid values are:<br /><br /> Append: The file send handler opens a file if it exists and appends a message to the end of the file. If the file does not exist, the file send handler creates a new file.<br /><br /> Overwrite: The file send handler opens a file if it exists and overwrites its content. If the file does not exist, the file send handler creates a new file.<br /><br /> Create new: If the file does not exist, the file send handler creates a file and writes to it. If the file already exists, the file send handler reports an error and then follows common adapter retry logic for send ports. This is a default copy mode for the file send handler.|  
|**Allow cache on write**|Define whether to use file system caching when writing a message to a file.<br /><br /> Options:<br /><br /> False. Do not use the file system cache.<br /><br /> True. Use the file system cache. **Important:**  Setting this property to True can increase the performance of the file adapter at the risk of potential data loss when there is a loss of power and not all data is written to disk.|  
|**Use temporary file while writing**|Defines whether to write the output file to a temporary file first and then rename the file once the write operation has completed. If this option is enabled then the temporary file will be created with the extension **BTS-WIP**.<br /><br /> Valid values are:<br /><br /> **True (checked)** The File adapter creates a temporary file when writing to the target folder.<br /><br /> **False (not checked)** The File adapter does not create a temporary file when writing to the target folder. **Note:**  This option is only available when the **CopyMode** property is set to a value of **Create new**.|  
  
## See Also  
 [How to Configure a File Receive Location](../Topic/How%20to%20Configure%20a%20File%20Receive%20Location.md)   
 [Restrictions on the File Mask and File Name Properties](../Topic/Restrictions%20on%20the%20File%20Mask%20and%20File%20Name%20Properties.md)   
 [Restrictions on Using Macros in File Names](../Topic/Restrictions%20on%20Using%20Macros%20in%20File%20Names.md)