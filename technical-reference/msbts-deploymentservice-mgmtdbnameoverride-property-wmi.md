---
description: "Learn more about: MSBTS_DeploymentService.MgmtDbNameOverride Property (WMI)"
title: MSBTS_DeploymentService.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_DeploymentService.MgmtDbNameOverride Property (WMI)
ms:assetid: 8b59bd12-41dd-4491-be3d-7507adee1082
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561282(v=BTS.80)
ms:contentKeyID: 51529556
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_DeploymentService.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

