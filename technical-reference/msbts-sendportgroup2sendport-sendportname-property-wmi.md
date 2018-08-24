---
title: MSBTS_SendPortGroup2SendPort.SendPortName Property (WMI)
TOCTitle: MSBTS_SendPortGroup2SendPort.SendPortName Property (WMI)
ms:assetid: e69760ec-a6fe-4695-a9ed-044e2dcb452f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561643(v=BTS.80)
ms:contentKeyID: 51533055
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPortGroup2SendPort.SendPortName Property (WMI)

 

Contains the name of the send port.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string SendPortGroup;  
```

## Remarks

This property is required for instance creation.

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **SendPortGroupName**, this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

