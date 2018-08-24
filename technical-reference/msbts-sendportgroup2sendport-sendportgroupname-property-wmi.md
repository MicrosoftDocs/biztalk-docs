---
title: MSBTS_SendPortGroup2SendPort.SendPortGroupName Property (WMI)
TOCTitle: MSBTS_SendPortGroup2SendPort.SendPortGroupName Property (WMI)
ms:assetid: b4fc74c9-9b0c-413e-92ab-b5acd8baedd6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578218(v=BTS.80)
ms:contentKeyID: 51530698
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendPortGroup2SendPort.SendPortGroupName Property (WMI)

 

Contains the name of the send port group.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string SendPortGroupName;  
```

## Remarks

This property is required for instance creation.

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, **MgmtDbServerOverride**, and **SendPortName**, this key forms a compound key for the class.

The maximum length for this property is 256 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

