---
title: MSBTS_AdapterSetting.DefaultInboundCfg Property (WMI)
TOCTitle: MSBTS_AdapterSetting.DefaultInboundCfg Property (WMI)
ms:assetid: 8f069e42-ad9b-46be-b1ac-5c41fa8d43a8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561341(v=BTS.80)
ms:contentKeyID: 51529637
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_AdapterSetting.DefaultInboundCfg Property (WMI)

 

Gets a default inbound configuration for the adapter.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string DefaultInboundCfg;  
```

## Remarks

This property is read-only.

The maximum length for this property is 1024 characters.

This configuration is used when a new [MSBTS\_ReceiveHandler](msbts-receivehandler-wmi.md) instance is created.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

