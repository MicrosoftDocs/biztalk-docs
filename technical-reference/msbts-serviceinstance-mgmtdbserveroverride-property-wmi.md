---
title: MSBTS_ServiceInstance.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_ServiceInstance.MgmtDbServerOverride Property (WMI)
ms:assetid: 64a02476-b038-4b07-b9f6-d86e84bb8eba
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560515(v=BTS.80)
ms:contentKeyID: 51528520
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServiceInstance.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use. The syntax shown is language neutral.

## Syntax

``` 
  
string MgmtDbNameOverride = "";  
```

## Remarks

This property is optional.

This property is read-only.

This property has a **Key** qualifier. Along with **InstanceID**, **MgmtDbNameOverride**, **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

