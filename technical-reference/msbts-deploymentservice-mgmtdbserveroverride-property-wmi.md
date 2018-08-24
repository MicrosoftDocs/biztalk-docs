---
title: MSBTS_DeploymentService.MgmtDbServerOverride Property (WMI)
TOCTitle: MSBTS_DeploymentService.MgmtDbServerOverride Property (WMI)
ms:assetid: fe86e809-5dc0-402a-ad67-863906ce78a9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa562150(v=BTS.80)
ms:contentKeyID: 51533797
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_DeploymentService.MgmtDbServerOverride Property (WMI)

 

Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.

*The syntax shown is language neutral.*

## Syntax

``` 
  
string MgmtDbServerOverride = "";  
```

## Remarks

This property is optional.

This property is read-write.

This property has a **Key** qualifier. Along with **MgmtDbNameOverride**, this key forms a compound key for the class.

The maximum length for this property is 80 characters.

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

