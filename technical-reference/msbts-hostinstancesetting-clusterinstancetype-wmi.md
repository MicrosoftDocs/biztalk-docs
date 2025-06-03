---
description: "Learn more about: MSBTS_HostInstanceSetting.ClusterInstanceType (WMI)"
title: MSBTS_HostInstanceSetting.ClusterInstanceType (WMI)
TOCTitle: MSBTS_HostInstanceSetting.ClusterInstanceType (WMI)
ms:assetid: 0e8c40a5-9c35-4159-bd5f-c8608e63ed03
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547376(v=BTS.80)
ms:contentKeyID: 51526218
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_HostInstanceSetting.ClusterInstanceType (WMI)

 

This property tells whether the BizTalk Host Instance NT service is clustered.

## Syntax

```C#
  
uint32ClusterInstanceType;  
```

## Return values

Possible values are:

0UnClusteredInstance

1ClusteredInstance

2ClusteredVirtualInstance

## Remarks

The default value for this parameter is 0.

This property is read only.

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

