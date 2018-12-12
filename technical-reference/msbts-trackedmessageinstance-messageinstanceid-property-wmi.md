---
title: MSBTS_TrackedMessageInstance.MessageInstanceID Property (WMI)
TOCTitle: MSBTS_TrackedMessageInstance.MessageInstanceID Property (WMI)
ms:assetid: eec5b1c3-9da1-4018-8c4b-56ceface2e26
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561807(v=BTS.80)
ms:contentKeyID: 51533281
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance.MessageInstanceID Property (WMI)

 

Contains the ID of the message instance.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MessageInstanceID;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **SourceDBName** and **SourceDBServerName**, this key forms a compound key for the class.

For sample code illustrating the **MSBTS\_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](saving-a-message-to-a-file-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

