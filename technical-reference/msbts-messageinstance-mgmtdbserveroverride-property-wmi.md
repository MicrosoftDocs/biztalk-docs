---
description: "Learn more about: MSBTS_MessageInstance.MgmtDbServerOverride Property (WMI)"
title: MSBTS_MessageInstance.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_MessageInstance.MgmtDbServerOverride Property (WMI)
ms:assetid: 3cf6c9d6-2ef0-4bba-9cfb-a8bd37de2011
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559706(v=BTS.80)
ms:contentKeyID: 51527442
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstance.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-only.

This property has a **Key** qualifier. Along with **MessageInstanceID**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **ServiceInstanceID**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

