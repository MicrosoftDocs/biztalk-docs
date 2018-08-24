---
title: MSBTS_TrackedMessageInstance.SourceDBName Property (WMI)
TOCTitle: MSBTS_TrackedMessageInstance.SourceDBName Property (WMI)
ms:assetid: 1e73e986-c287-41be-84b6-9287c5acbd91
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559116(v=BTS.80)
ms:contentKeyID: 51526683
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance.SourceDBName Property (WMI)

 

Contains the name of the SQL database where the tracked message is stored, either the MessageBox or Archived database.

## Property Declaration

*The syntax shown is language neutral.*

``` 
string SourceDBName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MessageInstanceID** and **SourceDBServerName**,this key forms a compound key for the class.

The maximum length for this property is 123 characters.

For sample code illustrating the **MSBTS\_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](saving-a-message-to-a-file-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

