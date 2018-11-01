---
title: MSBTS_TrackedMessageInstance.SaveToFile Method (WMI)
TOCTitle: MSBTS_TrackedMessageInstance.SaveToFile Method (WMI)
ms:assetid: 0a96576c-75b4-452e-bd5b-9f587726c502
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547235(v=BTS.80)
ms:contentKeyID: 51526118
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance.SaveToFile Method (WMI)

 

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

\[in\] Describes the full path for the folder that will contain the output files.

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

For sample code illustrating the **MSBTS\_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](saving-a-message-to-a-file-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

