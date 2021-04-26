---
description: "Learn more about: Troubleshooting the Adapter"
title: "Troubleshooting the Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "wildcard characters, in send port properties"
  - "troubleshooting adapter"
  - "Get.xml"
  - "send ports, using wildcards in properties"
ms.assetid: e9e0408f-5a12-4f05-83a6-37dc519ae4c5
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting the Microsoft BizTalk Adapter for PeopleSoft Enterprise
This topic contains information to help you identify and resolve issues that you might experience while you are using Microsoft BizTalk Adapter for PeopleSoft Enterprise.  
  
## Cannot use wildcard characters in send port properties  
 BizTalk Adapter for PeopleSoft Enterprise does not support using wildcard characters in the following send port property fields:  
  
-   Username  
  
-   App Server Path  
  
-   Java_Home  
  
-   People JAR Files  
  
## Get.xml data assigns 0001-01-01 value for null dates  
 Get.xml incorrectly assigns 0001-01-01 value for null dates. You must use the BizTalk Mapper tool if you want to replace the 0001-01-01 with null.  
  
## Creating and updating properties with collections fails  
 When using the Adapter with PeopleSoft version 8.17.02, the Adapter can read data from PeopleSoft server correctly. However, creating and updating fails for properties with collections. This is a known PeopleSoft issue that may be fixed in a future release of PeopleSoft.  
  
## See Also  
 [Troubleshooting PeopleSoft](../core/troubleshooting-peoplesoft.md)
