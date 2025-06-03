---
description: "Learn more about: MSBTS_SendPort.ReceivePipeline Property (WMI)"
title: MSBTS_SendPort.ReceivePipeline Property (WMI)
TOCTitle: MSBTS_SendPort.ReceivePipeline Property (WMI)
ms:assetid: 46be81e8-ed56-4d56-aeb2-49ff4464c1bd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559891(v=BTS.80)
ms:contentKeyID: 51527756
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_SendPort.ReceivePipeline Property (WMI)

 

Contains the name of the receive pipeline for the port.

*The syntax shown is language neutral.*

## Syntax

```C#
string ReceivePipeline;  
```

## Remarks

This property is required for instance creation for solicit-response (two-way) send ports. This property is writeable at instance creation. After instance creation, this property is read-only.

The maximum length for this property is 256 characters.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.ReceivePipeline** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

