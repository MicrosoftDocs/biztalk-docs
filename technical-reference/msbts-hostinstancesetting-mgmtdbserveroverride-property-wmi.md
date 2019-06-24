---
title: MSBTS_HostInstanceSetting.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_HostInstanceSetting.MgmtDbServerOverride Property (WMI)
ms:assetid: e8976a17-0368-483d-a2b5-902336812ca3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561682(v=BTS.80)
ms:contentKeyID: 51533116
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstanceSetting.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

## Property Declaration

*The syntax shown is language neutral.*

```C#
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **Name** and **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

