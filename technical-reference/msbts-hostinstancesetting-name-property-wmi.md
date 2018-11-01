---
title: MSBTS_HostInstanceSetting.Name Property (WMI)
TOCTitle: MSBTS_HostInstanceSetting.Name Property (WMI)
ms:assetid: 6a3bcfcd-3fa9-41d1-9d46-d663a4ef68fb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560632(v=BTS.80)
ms:contentKeyID: 51528678
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstanceSetting.Name Property (WMI)

 

Contains the name of the host instance.

## Property Declaration

*The syntax shown is language neutral.*

``` 
string Name;  
```

## Remarks

This property is read-only.

The value of **Name** is unique in the BizTalk group.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.

The maximum length for this property is 128 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

