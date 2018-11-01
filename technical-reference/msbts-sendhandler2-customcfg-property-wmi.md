---
title: MSBTS_SendHandler2.CustomCfg Property (WMI)
TOCTitle: MSBTS_SendHandler2.CustomCfg Property (WMI)
ms:assetid: 0f85d38b-f58f-4034-92f4-eb894043c9ea
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547539(v=BTS.80)
ms:contentKeyID: 51526253
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendHandler2.CustomCfg Property (WMI)

 

This property contains adapter-specific configuration in XML format.

## Syntax

``` 
  
stringCustomCfg;  
```

## Remarks

An empty value for this property means that adapter lacks some important information and won't function correctly.

This property is read/write.

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

