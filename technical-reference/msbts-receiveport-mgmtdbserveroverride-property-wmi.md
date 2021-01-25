---
description: "Learn more about: MSBTS_ReceivePort.MgmtDbServerOverride Property (WMI)"
title: MSBTS_ReceivePort.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_ReceivePort.MgmtDbServerOverride Property (WMI)
ms:assetid: 689aadbf-db55-46cc-a40a-1f254c9acc38
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560583(v=BTS.80)
ms:contentKeyID: 51528630
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceivePort.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

