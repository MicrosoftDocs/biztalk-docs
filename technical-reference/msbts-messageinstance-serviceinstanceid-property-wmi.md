---
title: MSBTS_MessageInstance.ServiceInstanceID Property (WMI)
TOCTitle: MSBTS_MessageInstance.ServiceInstanceID Property (WMI)
ms:assetid: 27bff459-aab7-4c87-b1a9-b42d7358f6bd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559286(v=BTS.80)
ms:contentKeyID: 51526866
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_MessageInstance.ServiceInstanceID Property (WMI)

 

Contains the ID of the service instance to which the message instance belongs.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string ServiceInstanceID;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MessageInstanceID**, **MgmtDbNameOverride**, and **MgmtDbServerOverride**, this key forms a compound key for the class.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

