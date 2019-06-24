---
title: MSBTS_GroupSetting.TrackingDBServerName Property (WMI)
TOCTitle: MSBTS_GroupSetting.TrackingDBServerName Property (WMI)
ms:assetid: 5d0d3a47-a454-4f50-9ba6-5d61b9c6016b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560378(v=BTS.80)
ms:contentKeyID: 51528337
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.TrackingDBServerName Property (WMI)

 

Gets the name of SQL Server where the tracking database is located.

The syntax shown is language neutral.

## Syntax

```C#
  
string TrackingDBServerName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

Maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

