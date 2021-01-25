---
description: "Learn more about: MSBTS_Host.Cluster Method (WMI)"
title: MSBTS_Host.Cluster Method (WMI)
TOCTitle: MSBTS_Host.Cluster Method (WMI)
ms:assetid: caa455d2-33f8-4383-ab5b-7025d12dd662
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547998(v=BTS.80)
ms:contentKeyID: 51531195
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host.Cluster Method (WMI)

 

This method clusters all BizTalk Host Instances on the given BizTalk Host.

## Syntax

```C#
  
uint32 Cluster(string ClusterResourceGroupName);  
```

#### Parameters

string ClusterResourceGroupName  
The cluster resource group name to be used.

## Property Value/Return Value

This method returns an HRESULT indicating whether the method completed successfully.

