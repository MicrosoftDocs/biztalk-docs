---
title: MSBTS_SendPort.SendPipeline Property (WMI)
TOCTitle: MSBTS_SendPort.SendPipeline Property (WMI)
ms:assetid: 9c39d383-22f5-4519-b0f9-72dcc65ee75c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577560(v=BTS.80)
ms:contentKeyID: 51529942
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort.SendPipeline Property (WMI)

 

Contains the name of the send pipeline for the port.

*The syntax shown is language neutral.*

## Syntax

```C#
string SendPipeline;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

The maximum length for this property is 256 characters.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.SendPipeline** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

