---
title: MSBTS_SendHandler.CustomCfg Property (WMI)
TOCTitle: MSBTS_SendHandler.CustomCfg Property (WMI)
ms:assetid: 91688ee0-8715-41be-b02a-adf386e5e090
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561390(v=BTS.80)
ms:contentKeyID: 51529705
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendHandler.CustomCfg Property (WMI)

 

Contains the adapter-specific configuration in XML format.

*The syntax shown is language neutral.*

## Syntax

```C#
  
string CustomCfg;  
```

## Remarks

An empty value indicates that the adapter lacks some important information and will not function correctly.

This property is optional.

This property is read-write.

For more information about the configuring the receive location of any of the native adapters, see the following topics:

  - [Configuring a File Send Handler](https://msdn.microsoft.com/library/aa577540\(v=bts.80\))

  - [Configuring an FTP Send Handler](https://msdn.microsoft.com/library/aa561311\(v=bts.80\))

  - [Configuring an HTTP Send Handler](https://msdn.microsoft.com/library/aa561097\(v=bts.80\))

  - [Configuring an SMTP Send Handler By Using BizTalk Explorer](https://msdn.microsoft.com/library/aa578257\(v=bts.80\))

  - [Configuring a SOAP Send Handler](https://msdn.microsoft.com/library/aa562126\(v=bts.80\))

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

