---
description: "Learn more about: MSBTS_GroupSetting.MgmtDbName Property (WMI)"
title: MSBTS_GroupSetting.MgmtDbName Property (WMI)
TOCTitle: MSBTS_GroupSetting.MgmtDbName Property (WMI)
ms:assetid: c1e56ac5-5fc7-4c09-ad18-1498c7c41327
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547827(v=BTS.80)
ms:contentKeyID: 51531073
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_GroupSetting.MgmtDbName Property (WMI)

 

Gets the initial catalog part of the BizTalk Management database connect string, and represents the database name.

The syntax shown is language neutral.

## Syntax

```C#
  
string MgmtDbName = "";  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbServerName**, this key forms a compound key for the class.

Maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

