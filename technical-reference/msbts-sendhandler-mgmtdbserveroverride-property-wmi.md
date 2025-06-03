---
description: "Learn more about: MSBTS_SendHandler.MgmtDbServerOverride Property (WMI)"
title: MSBTS_SendHandler.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_SendHandler.MgmtDbServerOverride Property (WMI)
ms:assetid: 6cffe8de-17d8-4f62-ad0c-110c4900c526
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560685(v=BTS.80)
ms:contentKeyID: 51528743
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_SendHandler.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **AdapterName** and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

