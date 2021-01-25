---
description: "Learn more about: MSBTS_Host.GetClusterResourceGroupNames (WMI)"
title: MSBTS_Host.GetClusterResourceGroupNames (WMI)
TOCTitle: MSBTS_Host.GetClusterResourceGroupNames (WMI)
ms:assetid: a6872748-cd0a-487a-acbe-69ae7e1a9d34
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577910(v=BTS.80)
ms:contentKeyID: 51530308
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.GetClusterResourceGroupNames (WMI)

 

This method returns a string array that contains a list of available cluster resource groups.

## Syntax

```C#
  
uint32 GetClusterResourceGroupNames(string[] ClusterResourceGroupNames);  
```

#### Parameters

string\[\] ClusterResourceGroupNames  
List of available cluster resource groups.

## Property Value/Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

