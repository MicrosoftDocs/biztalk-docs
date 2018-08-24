---
title: MSBTS_GroupSetting.ConfigurationCacheRefreshInterval Property (WMI)
TOCTitle: MSBTS_GroupSetting.ConfigurationCacheRefreshInterval Property (WMI)
ms:assetid: e51e7730-3fa6-4d9c-b268-d54372fda962
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561618(v=BTS.80)
ms:contentKeyID: 51532996
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.ConfigurationCacheRefreshInterval Property (WMI)

 

Gets or sets a value indicating how often BizTalk Server refreshes the cache of the messaging configuration objects, in seconds.

The syntax shown is language neutral.

## Syntax

``` 
  
uint32 ConfigurationCacheRefreshInterval = 60;  
```

## Remarks

This property is read-write.

Maximum value for this property is 43200 and minimum value is 1.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

