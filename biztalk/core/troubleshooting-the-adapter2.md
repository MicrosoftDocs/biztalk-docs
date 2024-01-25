---
description: "Learn how to identify and resolve issues that you might experience while using Microsoft BizTalk Adapter for PeopleSoft Enterprise."
title: "Troubleshooting the Adapter2"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
