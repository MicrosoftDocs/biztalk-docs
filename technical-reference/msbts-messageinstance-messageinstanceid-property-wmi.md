---
title: MSBTS_MessageInstance.MessageInstanceID Property (WMI)
TOCTitle: MSBTS_MessageInstance.MessageInstanceID Property (WMI)
ms:assetid: ed45b52b-a871-443e-a899-133f20ac0d2a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561782(v=BTS.80)
ms:contentKeyID: 51533247
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstance.MessageInstanceID Property (WMI)

 

Contains the ID of the message instance.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MessageInstanceID;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **ServiceInstanceID**, this key forms a compound key for the class.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

