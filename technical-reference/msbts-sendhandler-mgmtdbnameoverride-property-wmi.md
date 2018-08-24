---
title: MSBTS_SendHandler.MgmtDbNameOverride Property (WMI)
TOCTitle: MSBTS_SendHandler.MgmtDbNameOverride Property (WMI)
ms:assetid: 0d49b360-8e8a-4cdc-a526-ed22dd3853b8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547349(v=BTS.80)
ms:contentKeyID: 51526183
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendHandler.MgmtDbNameOverride Property (WMI)

 

Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbServerOverride** and **AdapterName**, this key forms a compound key for the class.

The maximum length for this property is 123 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

