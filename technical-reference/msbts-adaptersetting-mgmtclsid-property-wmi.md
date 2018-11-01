---
title: MSBTS_AdapterSetting.MgmtCLSID Property (WMI)
TOCTitle: MSBTS_AdapterSetting.MgmtCLSID Property (WMI)
ms:assetid: 9a48c1bf-7ad8-4f23-a7b3-fac1d1a6146e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577518(v=BTS.80)
ms:contentKeyID: 51529890
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_AdapterSetting.MgmtCLSID Property (WMI)

 

Gets the class identifier (CLSID) of the COM component responsible for managing this adapter.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtCLSID;  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

