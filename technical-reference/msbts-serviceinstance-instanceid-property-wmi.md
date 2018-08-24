---
title: MSBTS_ServiceInstance.InstanceID Property (WMI)
TOCTitle: MSBTS_ServiceInstance.InstanceID Property (WMI)
ms:assetid: 587ae471-50ef-4f43-9f88-f2c434c29e40
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560279(v=BTS.80)
ms:contentKeyID: 51528206
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServiceInstance.InstanceID Property (WMI)

 

Contains the ID of the service instance to which this message belongs. The syntax shown is language neutral.

## Syntax

``` 
  
string InstanceID;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, this key forms a compound key for the class.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

