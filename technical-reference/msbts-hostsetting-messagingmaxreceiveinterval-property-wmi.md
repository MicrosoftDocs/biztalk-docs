---
description: "Learn more about: MSBTS_HostSetting.MessagingMaxReceiveInterval Property (WMI)"
title: MSBTS_HostSetting.MessagingMaxReceiveInterval Property (WMI)
TOCTitle: MSBTS_HostSetting.MessagingMaxReceiveInterval Property (WMI)
ms:assetid: 06784349-d6e8-471c-8c12-3aa63dcaea7b
ms:mtpsurl: https://msdn.microsoft.com/library/Gg678620(v=BTS.80)
ms:contentKeyID: 51526016
ms.date: 08/30/2017
mtps_version: v=BTS.80
dev_langs:
- vb
ms.topic: reference
---

# MSBTS\_HostSetting.MessagingMaxReceiveInterval Property (WMI)

 

This property is the maximum polling interval in milliseconds that the BizTalk host instance looks for new messages. Allowed values are 50 to int max.

## Syntax

``` vb
uint32  MessagingMaxReceiveInterval;  
```

## Remarks

This property is read/write.

The default value for this property is 500.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

