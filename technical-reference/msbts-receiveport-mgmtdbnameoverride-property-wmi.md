---
title: MSBTS_ReceivePort.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_ReceivePort.MgmtDbNameOverride Property (WMI)
ms:assetid: eb1235e3-b657-4618-a7cb-6361450f067d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561738(v=BTS.80)
ms:contentKeyID: 51533189
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceivePort.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

