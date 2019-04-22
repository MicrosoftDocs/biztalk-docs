---
title: MSBTS_TrackedMessageInstance.SourceDBServerName Property (WMI)
TOCTitle: MSBTS_TrackedMessageInstance.SourceDBServerName Property (WMI)
ms:assetid: 8325e1d9-a97c-4bc5-8e4f-5a872371c4a1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561127(v=BTS.80)
ms:contentKeyID: 51529346
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance.SourceDBServerName Property (WMI)

 

Contains the name of the SQL Server where the tracked message is stored, either the MessageBox or Archived database.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string SourceDBServerName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MessageInstanceID** and **SourceDBName**, this key forms a compound key for the class.

The maximum value for this property is 80 characters.

For sample code illustrating the **MSBTS\_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](saving-a-message-to-a-file-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

