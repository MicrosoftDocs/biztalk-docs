---
title: "Configuring Service Encodings | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1f0dc56-dad8-4fcd-9e61-f84699b0942b
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Configuring Service Encodings
The DRDA Service maps code pages and supports custom code page conversions using an underlying HIS Encoder component and the Windows National Language Support (NLS) system components.  
  
### Custom NLS Code Pages  
 Using Microsoft Windows Update, you can install additional Windows language packs that include Windows NLS code page conversion libraries. Optionally, the HIS Encoder can load a custom NLS code page based on codePage elements defined within the codePages portion of the MsDrdaService.exe.config file.  
  
#### Code Page Number  
 The **number** attribute instructs the HIS Encoder to load a custom NLS code page file. This **optional** attribute accepts an **integer**. The default value is **0**.  
  
#### Code Page Name  
 The **name** attribute names the custom NLS code page that the HIS Encoder should load based on the defined custom NLS code page number. This **optional** attribute accepts a **string**. The default value is an **empty string**.  
  
#### Code Page Description  
 The **description** attribute describes the custom NLS code page that the HIS Encoder should load based on the defined custom NLS code page number. This **optional** attribute accepts a **string**. The default value is an **empty string**.  
  
#### NLS Code Page Number  
 The **nlsCodePage** attribute defines which standard NLS code page number that the HIS Encoder should replace with the custom code page number. This **optional** attribute accepts an **integer**. The default value is **0**.  
  
 For example, to replace the standard NLS code page for “EBCDIC - U.S./ Canada (Euro)” CCSID 1140 with a custom NLS code page “EBCDIC US Custom” custom code page file 21140.nls and custom code page number 21140, specify the following.  
  
```  
<codePage number="21140"   
                name="Custom21140"   
                description="Custom codepage based on 1140"   
                nlsCodePage="1140">  
```  
  
### Custom Code Point Mappings  
 The HIS Encoder can custom map code points within standard NLS and custom NLS code pages based on ebcdicToUnicodeConversion elements defined within the codePages portion of the MsDrdaService.exe.config file.  
  
#### EBCDIC to UNICODE  
 The “**from**” and “**to**” attributes within an **ebcdicToUnicode** element instruct the HIS Encoder to convert from and to these code points. This **optional** attribute accepts a **string** value, in the form of a hex code point value.  
  
 The **reversible** attribute instructs the HIS Encoder to convert in the reversible direction. This **optional** attribute accepts a **Boolean** value. The default is **false**.  
  
#### UNICODE to EBCDIC  
 The “**from**” and “**to**” attributes within a **unicodeToEbcdic** element instruct the HIS Encoder to convert from and to these code points. This **optional** attribute accepts a **string** value, in the form of a hex code point value.  
  
 The **reversible** attribute instructs the HIS Encoder to convert in the reversible direction. This **optional** attribute accepts a **Boolean** value. The default is **false**.  
  
### Conversion Behavior  
 The HIS Encoder is shared by a number of Microsoft Host Integration Server 2013 features, including the DRDA Service and Transaction Integrator. The **conversionBehavior** element is for use by Transaction Integrator only. The DRDA Service does not require this element.