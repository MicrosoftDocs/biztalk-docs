---
description: "Learn more about: MSBTS_ServerSetting.MgmtDbServerOverride Property (WMI)"
title: MSBTS_ServerSetting.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_ServerSetting.MgmtDbServerOverride Property (WMI)
ms:assetid: 5c2495a9-3981-4da3-8240-e172419c5e14
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560361(v=BTS.80)
ms:contentKeyID: 51528300
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ServerSetting.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

