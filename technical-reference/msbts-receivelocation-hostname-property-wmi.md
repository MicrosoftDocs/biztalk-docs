---
title: MSBTS_ReceiveLocation.HostName Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.HostName Property (WMI)
ms:assetid: ab183931-c3d0-4e43-ad51-a2b6db56510e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577991(v=BTS.80)
ms:contentKeyID: 51530434
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation.HostName Property (WMI)

 

Contains the name of the receive handler used by the receive location.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string HostName;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

