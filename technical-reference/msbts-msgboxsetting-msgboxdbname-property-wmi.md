---
description: "Learn more about: MSBTS_MsgBoxSetting.MsgBoxDBName Property (WMI)"
title: MSBTS_MsgBoxSetting.MsgBoxDBName Property (WMI)
TOCTitle: MSBTS_MsgBoxSetting.MsgBoxDBName Property (WMI)
ms:assetid: 61484743-9e16-465b-be0e-c085f82a3ce3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560455(v=BTS.80)
ms:contentKeyID: 51528435
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MsgBoxSetting.MsgBoxDBName Property (WMI)

 

Contains the name of the MessageBox setting database.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MsgBoxDBName;  
```

## Remarks

This property is read-only.

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **MsgBoxDBServerName**, this key forms a compound key for the class.

The maximum length for this property is 100 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

