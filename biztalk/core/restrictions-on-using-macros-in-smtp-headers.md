---
title: "Restrictions on Using Macros in SMTP Headers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuring [SMTP adapters], restrictions"
  - "macros, SMTP headers [SMTP adapters]"
  - "SMTP adapters, macros"
  - "SMTP adapters, restrictions"
  - "configuring [SMTP adapters], SMTP headers"
  - "SMTP adapters, SMTP headers"
  - "configuring [SMTP adapters], macros"
  - "SMTP headers"
ms.assetid: ceab0917-cb3c-423b-a15f-63747ab1d8da
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restrictions on Using Macros in SMTP Headers
You can form the **Subject**, **To**, **From**, and **CC** properties on an SMTP message header dynamically by using a predefined set of macros. Before sending a message, the SMTP send handler substitutes all the macros in headers with their values. You can use several different macros when forming one header.  
  
 The SMTP send handler does not substitute macros in the **To**, **From**, or **CC** header if any of the following are true:  
  
- The corresponding system property is not set.  
  
- The macro is misspelled.  
  
- The value for the macro contains symbols that are not valid for the SMTP headers.  
  
  If any of these conditions are met, the SMTP send handler leaves the macros as they are, for example, <strong>%SourceParty%@somedomain.com</strong> or **Message from %SourceParty%**.  
  
  The following table lists the macros you can use to build the **To**, **CC**, and **Subject** headers.  
  
|Macro|Description|For use with To|For use with CC|For use with Subject|  
|-----------|-----------------|---------------------|---------------------|--------------------------|  
|%MessageID%|Globally unique identifier (GUID) of the message in BizTalk Server. The value comes from the message context property **BTS.MessageID**.|No|No|Yes|  
|%datetime_bts2000%|UTC date time in the format YYYYMMDDhhmmsss, where sss means seconds and milliseconds (for example, 199707121035234 means 1997/07/12, 10:35:23 and 400 milliseconds).|No|No|Yes|  
|%datetime%|UTC date time in the format YYYY-MM-DDThhmmss (for example, 1997-07-12T103508).|No|No|Yes|  
|%datetime.tz%|Local date time plus time zone from GMT in the format YYYY-MM-DDThhmmssTZD, (for example, 1997-07-12T103508+800).|No|No|Yes|  
|%time%|UTC time in the format hhmmss.|No|No|Yes|  
|%time.tz%|Local time plus time zone from GMT in the format hhmmssTZD (for example, 124525+530).|No|No|Yes|  
|%SourceParty%|Name of the source party from which the File adapter received the message.|No|No|Yes|  
|%SourcePartyQualifier%|Qualifier of the source party from which the File adapter received the message.|No|No|Yes|  
|%DestinationParty%|Name of the destination party. The value comes from the message context property **BTS.DestinationParty**.|Yes|Yes|Yes|  
|%DestinationPartyQualifier%|Qualifier of the destination party. The value comes from the message context property **BTS.DestinationPartyQualifier**.|No|No|Yes|  
  
## See Also  
 [Restrictions When Configuring the SMTP Adapter](../core/restrictions-when-configuring-the-smtp-adapter.md)