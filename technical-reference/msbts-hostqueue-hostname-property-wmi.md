---
title: MSBTS_HostQueue.HostName Property (WMI)
TOCTitle: MSBTS_HostQueue.HostName Property (WMI)
ms:assetid: 5e1d8796-ded8-405f-863a-510af0243c9b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560402(v=BTS.80)
ms:contentKeyID: 51528355
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostQueue.HostName Property (WMI)

 

Contains the name of the host that this queue corresponds to.


> [!NOTE]
> <P>The syntax shown is language neutral.</P>



## Syntax

``` 
  
string HostName;  
```

## Remarks

This property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

