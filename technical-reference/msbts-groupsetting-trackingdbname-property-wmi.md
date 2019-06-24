---
title: MSBTS_GroupSetting.TrackingDBName Property (WMI)
TOCTitle: MSBTS_GroupSetting.TrackingDBName Property (WMI)
ms:assetid: 8918c27c-f5a1-4602-8718-7c7ccaf3da4a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561242(v=BTS.80)
ms:contentKeyID: 51529508
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.TrackingDBName Property (WMI)

 

Gets the name of the tracking SQL database.

The syntax shown is language neutral.

## Syntax

```C#
  
string TrackingDBName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

Maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

