---
description: "Learn more about: MSBTS_HostInstanceSetting.MgmtDbNameOverride Property (WMI)"
title: MSBTS_HostInstanceSetting.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_HostInstanceSetting.MgmtDbNameOverride Property (WMI)
ms:assetid: 614a42d2-1fff-404d-bf1a-c3b0937e886a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560456(v=BTS.80)
ms:contentKeyID: 51528447
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstanceSetting.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

