---
title: MSBTS_SendPortGroup.Name Property (WMI)
TOCTitle: MSBTS_SendPortGroup.Name Property (WMI)
ms:assetid: 9a2b2e31-c75b-4f29-b0d2-ca927b449cd8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577515(v=BTS.80)
ms:contentKeyID: 51529887
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPortGroup.Name Property (WMI)

 

Contains the name of the send port group.

*The syntax shown is language neutral.*

## Syntax

```C#
string Name;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDBServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 256 characters.

This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPortGroup.Name** property.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

