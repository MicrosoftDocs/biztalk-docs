---
title: MSBTS_GroupSetting.MgmtDbServerName Property (WMI)
TOCTitle: MSBTS_GroupSetting.MgmtDbServerName Property (WMI)
ms:assetid: 9ade20a9-9ddf-401b-b15e-63dd8ab86736
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577538(v=BTS.80)
ms:contentKeyID: 51529971
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting.MgmtDbServerName Property (WMI)

 

Gets the data source part of the BizTalk Management database connect string.

The syntax shown is language neutral.

## Syntax

``` 
  
string MgmtDbServerName = "";  
```

## Remarks

This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.

This property has a **Key** qualifier. Along with **MgmtDbName**, this key forms a compound key for the class.

Maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

