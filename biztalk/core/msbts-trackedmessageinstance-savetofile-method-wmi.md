---
title: "MSBTS_TrackedMessageInstance.SaveToFile Method (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a96576c-75b4-452e-bd5b-9f587726c502
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_TrackedMessageInstance.SaveToFile Method (WMI)
Saves the message context and parts into multiple output files.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
uint32 SaveToFile(  
     string OutputFolderFullPath  
);  
```  
  
## Parameters  
 *OutputFolderFullPath*  
  
 [in] Describes the full path for the folder that will contain the output files.  
  
## Return Value  
 This method returns an HRESULT indicating whether the method completed successfully.  
  
## Remarks  
 For sample code illustrating the **MSBTS_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](../core/saving-a-message-to-a-file-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.