---
description: "Learn more about: How to Distribute the Web Setup Package"
title: "How to Distribute the Web Setup Package | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, Web services"
  - "Web services, distributing"
  - "Web services, deploying"
ms.assetid: 0db71fdf-80d9-4ad5-b0d4-730d0bb549d4
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Distribute the Web Setup Package
After you create the installation package, you need to create a distribution folder where a MSI file and a BindingInfo.xml file are copied to set up the Web service.  
  
### To distribute the Web setup package  
  
1.  Create a distribution folder to contain your setup files.  
  
2.  Copy the .MSI file from the Web Setup project output folder to the distribution folder.  
  
3.  Copy the BindingInfo.xml file from the temp folder in the ASP.NET Web Service project folder to the distribution folder.  
  
## See Also  
 [Deploying Published Web Services on a Non-Visual Studio Computer](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)
