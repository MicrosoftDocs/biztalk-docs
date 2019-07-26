---
title: MSBTS_SendPortGroup.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_SendPortGroup.MgmtDbServerOverride Property (WMI)
ms:assetid: f0d85279-b702-4573-a95a-54f2f9560f6a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561851(v=BTS.80)
ms:contentKeyID: 51533314
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPortGroup.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **Name**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

