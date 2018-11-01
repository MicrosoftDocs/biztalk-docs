---
title: MSBTS_HostInstance.ClusterInstanceType Property (WMI)
TOCTitle: MSBTS_HostInstance.ClusterInstanceType Property (WMI)
ms:assetid: add87697-1a91-4f10-b278-2f71283444c7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578062(v=BTS.80)
ms:contentKeyID: 51530510
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance.ClusterInstanceType Property (WMI)

 

This property tells whether the BizTalk Host Instance NT service is clustered.

## Syntax

``` 
  
uint32ClusterInstanceType;  
```

## Return Value

The return value can be one of the following:

0UnClusteredInstance

1 ClusteredInstance

2ClusteredVirtualInstance

## Remarks

The default value for this parameter is 0.

This property is read only.

The syntax shown is language neutral.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

