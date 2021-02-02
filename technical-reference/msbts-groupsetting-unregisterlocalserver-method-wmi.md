---
description: "Learn more about: MSBTS_GroupSetting.UnRegisterLocalServer Method (WMI)"
title: MSBTS_GroupSetting.UnRegisterLocalServer Method (WMI)
TOCTitle: MSBTS_GroupSetting.UnRegisterLocalServer Method (WMI)
ms:assetid: f20282a5-d710-4dbf-b01e-f9ed5d08c967
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561882(v=BTS.80)
ms:contentKeyID: 51533346
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.UnRegisterLocalServer Method (WMI)

 

Deletes the Windows NT registry information set up by the **RegisterLocalServer** method.

The syntax shown is language neutral.

## Syntax

```C#
  
uint32 UnRegisterLocalServer();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

This method should only be invoked internally by BizTalk Server

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

