---
description: "Learn more about: MSBTS_SendPort.MgmtDbNameOverride Property (WMI)"
title: MSBTS_SendPort.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_SendPort.MgmtDbNameOverride Property (WMI)
ms:assetid: 7214b150-986f-4611-b087-1dbce088dc4a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560791(v=BTS.80)
ms:contentKeyID: 51528902
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

