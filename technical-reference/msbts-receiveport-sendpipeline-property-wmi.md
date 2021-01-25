---
description: "Learn more about: MSBTS_ReceivePort.SendPipeline Property (WMI)"
title: MSBTS_ReceivePort.SendPipeline Property (WMI)
TOCTitle: MSBTS_ReceivePort.SendPipeline Property (WMI)
ms:assetid: 6442bab4-6d49-4285-a2d0-d45fcbdea3fe
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560505(v=BTS.80)
ms:contentKeyID: 51528536
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceivePort.SendPipeline Property (WMI)

 

Contains the name of the send pipeline for the port.

*The syntax shown is language neutral.*

## Syntax

```C#
string SendPipeline;  
```

## Remarks

The maximum length for this property is 256 characters.

This property is required for instance creation for a request-response (two-way) receive port. This property is writeable at instance creation. After instance creation, this property is read-only.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceivePort.SendPipeline** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

