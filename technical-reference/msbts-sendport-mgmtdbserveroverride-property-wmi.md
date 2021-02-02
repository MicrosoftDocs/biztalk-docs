---
description: "Learn more about: MSBTS_SendPort.MgmtDbServerOverride Property (WMI)"
title: MSBTS_SendPort.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_SendPort.MgmtDbServerOverride Property (WMI)
ms:assetid: 091575b1-273f-4c54-bf03-2a040fce9879
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547103(v=BTS.80)
ms:contentKeyID: 51526080
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPort.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

