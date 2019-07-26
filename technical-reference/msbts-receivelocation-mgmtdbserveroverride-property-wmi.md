---
title: MSBTS_ReceiveLocation.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_ReceiveLocation.MgmtDbServerOverride Property (WMI)
ms:assetid: 66ba109c-70a6-43ee-88c6-6bb1806f77f5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560548(v=BTS.80)
ms:contentKeyID: 51528599
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocation.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride, ReceivePortName**, and **Name**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

