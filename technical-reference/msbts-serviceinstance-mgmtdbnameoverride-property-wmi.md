---
description: "Learn more about: MSBTS_ServiceInstance.MgmtDbNameOverride Property (WMI)"
title: MSBTS_ServiceInstance.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_ServiceInstance.MgmtDbNameOverride Property (WMI)
ms:assetid: 149f6d5d-e75f-44ad-834d-67b2cade09d3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558696(v=BTS.80)
ms:contentKeyID: 51526376
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_ServiceInstance.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use. The syntax shown is language neutral.

## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-only.

This property has a **Key** qualifier. Along with **InstanceID**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

