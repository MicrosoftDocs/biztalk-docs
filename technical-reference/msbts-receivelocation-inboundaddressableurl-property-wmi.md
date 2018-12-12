---
title: MSBTS_ReceiveLocation.InboundAddressableURL Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.InboundAddressableURL Property (WMI)
ms:assetid: 396a28bc-5f53-4e24-be7f-7dc12d77140f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559630(v=BTS.80)
ms:contentKeyID: 51527345
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation.InboundAddressableURL Property (WMI)

 

Contains a URL that can be used by external parties to send documents to the receive location.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string InboudAddressableURL;  
```

## Remarks

This property is read-write.

Value of this property is usually provided by the transport component, based on the adapter-specific configuration.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

