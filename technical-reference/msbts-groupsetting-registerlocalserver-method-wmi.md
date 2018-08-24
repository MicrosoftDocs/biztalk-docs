---
title: MSBTS_GroupSetting.RegisterLocalServer Method (WMI)
TOCTitle: MSBTS_GroupSetting.RegisterLocalServer Method (WMI)
ms:assetid: 17a26237-b546-45b3-b297-6758ecc4ea6a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa558781(v=BTS.80)
ms:contentKeyID: 51526472
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.RegisterLocalServer Method (WMI)

 

Sets up the Windows NT registry of the local computer to point to this BizTalk group.

The syntax shown is language neutral.

## Syntax

``` 
  
uint32 RegisterLocalServer();  
```

## Return Value

This method returns an HRESULT indicating whether the method completed successfully.

## Remarks

This method should only be invoked internally by BizTalk Server.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

