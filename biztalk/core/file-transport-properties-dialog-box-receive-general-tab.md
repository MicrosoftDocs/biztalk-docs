---
title: "File Transport Properties Dialog Box, Receive, General Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.file.transport.receive.general"
helpviewer_keywords: 
  - "file transport, properties"
  - "file transport, configuring"
  - "configuring, file transport"
ms.assetid: cd3061d7-9ef7-4a26-8809-fe394f97f064
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# File Transport Properties Dialog Box, Receive, General Tab
Use the **General** tab to configure the receive location for the File adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Receive folder**|Required. Specify the path to a folder on the file system or network share from where the file receive handler reads files. The path can be entered directly into the Receive folder text box or can be selected from the file system by navigating to the folder with the Browse button. When browsing for the folder in the Browse For Folder dialog box you also have the option to create a new folder by clicking the Make New Folder button.<br /><br /> Type: String **Note:**  Do not set the Receive folder property to a folder that uses the NT Distributed File System with a symbolic link. If you are using an NT Distributed File System, you can only use folders with straight network paths in File Adapter Receive Locations.|  
|**File mask**|Required. Specify the mask for the files. This mask can contain the standard wildcard value (*).<br /><br /> Default value: \*.xml<br /><br /> Type: String|  
|**Public address**|Specify the public address of this location. This address is exposed to external partners.<br /><br /> If this property is not specified, then the run-time engine replaces it as:<br /><br /> file://\<Receive folder>/\<File mask><br /><br /> The value for this property requires an adapter prefix.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256|  
|**Retry count**|Specify the number of attempts to access the receive location on a network share if it is temporarily unavailable.<br /><br /> Default Value: 5<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: MAX_LONG|  
|**Retry interval (min)**|Specify the retry interval time (in minutes) between attempts to access the receive location on the network share if it is temporarily unavailable.<br /><br /> Default Value: 5 minutes<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: MAX_LONG|  
|||  
  
## See Also  
 [How to Configure a File Receive Location](../Topic/How%20to%20Configure%20a%20File%20Receive%20Location.md)   
 [Restrictions on the File Mask and File Name Properties](../Topic/Restrictions%20on%20the%20File%20Mask%20and%20File%20Name%20Properties.md)