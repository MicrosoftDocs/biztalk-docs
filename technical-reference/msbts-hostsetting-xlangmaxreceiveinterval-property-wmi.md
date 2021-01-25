---
description: "Learn more about: MSBTS_HostSetting.XlangMaxReceiveInterval Property (WMI)"
title: MSBTS_HostSetting.XlangMaxReceiveInterval Property (WMI)
TOCTitle: MSBTS_HostSetting.XlangMaxReceiveInterval Property (WMI)
ms:assetid: 5e6a5762-49f7-4db3-b07d-9d8c13de320f
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678629(v=BTS.80)
ms:contentKeyID: 51528378
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
---

# MSBTS\_HostSetting.XlangMaxReceiveInterval Property (WMI)

 

This property is the maximum polling interval in milliseconds that the BizTalk host instance looks for new messages in XLANG. Allowed values are 50 to int max.

## Syntax

``` vb
uint32  XlangMaxReceiveInterval;  
```

## Remarks

This property is read/write.

The default value for this property is 500.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

