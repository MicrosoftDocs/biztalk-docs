---
title: MSBTS_ReceiveLocation.InboundTransportURL Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.InboundTransportURL Property (WMI)
ms:assetid: 953404c9-13f4-4e44-845e-285b80c84f0f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577422(v=BTS.80)
ms:contentKeyID: 51529794
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation.InboundTransportURL Property (WMI)

 

Contains an adapter-specific URL which the given instance of the receive location is listening to.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string InboundTransportURL;  
```

## Remarks

This property is read-write.

This property is required for instance creation.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

