---
title: "EDI Character Set Support | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4f4492b-8cbe-48ed-810a-3e73e1cb5996
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Character Set Support
This topic indicates which character sets are supported in the EDI features of [!INCLUDE[prague](../includes/prague-md.md)].  
  
|EDI Encoding|Supported Character Sets|  
|------------------|------------------------------|  
|X12 (including HIPAA)|X12 - Basic character set (subset of ASCII)|  
|-|X12- Extended character set (subset of ASCII and also includes ISO8859-1 chars)|  
|-|UTF8/UNICODE|  
|EDIFACT|UNOA|  
|-|UNOB|  
|-|UNOC- ISO 8859-1 : Information processing - Part 1: Latin alphabet No. 1|  
|-|KECA - KS_C_5601-1987 (Windows 949 Code page)|  
|-|UNOX (ISO2022 – JP)|  
|-|UNOY- UTF8 encoded data **Note:**  The UNOD through UNOK character sets that support UTF8 encoded data are also supported.|  
  
## Setting the EDI Character Set  
 For X12 encoded interchanges, you can set the character set for a pipeline by setting the CharacterSet pipeline property. For more information, see [Configuring EDI Pipeline Properties](../core/configuring-edi-pipeline-properties.md).  
  
> [!NOTE]
>  There is an X12 character set control in the X12 Interchange Envelope Generation page of the X12 EDI Properties dialog box in the BizTalk Server Administration console, but that control is only used to validate the values entered for the properties in the EDI Properties dialog box.  
  
 For EDIFACT encoded interchanges, you can set the character set for a party by setting the UNB1.1 party property in the UNB Segment Definition property page for the party as interchange receiver. The encoding used in an incoming interchange is determined by the value of the UNB1.1 field in the header of the interchange. For more information, see [Configuring Envelopes (EDIFACT-Transaction Set Settings)](../core/configuring-envelopes-edifact-transaction-set-settings.md).  
  
## See Also  
 [Configuring EDI Pipeline Properties](../core/configuring-edi-pipeline-properties.md)   
 [Configuring Envelopes (EDIFACT-Transaction Set Settings)](../core/configuring-envelopes-edifact-transaction-set-settings.md)