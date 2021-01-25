---
description: "Learn more about: MSBTS_SendPortGroup2SendPort.MgmtDbNameOverride Property (WMI)"
title: MSBTS_SendPortGroup2SendPort.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_SendPortGroup2SendPort.MgmtDbNameOverride Property (WMI)
ms:assetid: 4df26909-3a20-41d4-afa5-56e7c7ac2106
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560067(v=BTS.80)
ms:contentKeyID: 51527926
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPortGroup2SendPort.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbServerOverride**, **SendPortGroupName**, and **SendPortName**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

