---
title: "How to Install the Web Setup Package | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, Web services"
  - "Web services, deploying"
  - "Web services, installing"
ms.assetid: c6b38a2f-ad07-4ccd-b267-9e3510df88c3
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install the Web Setup Package
Use the contents of the distribution folder to setup the Web service on a destination computer.  
  
### To install the Web setup package  
  
1.  Copy the distribution folder onto the destination computer.  
  
    > [!IMPORTANT]
    >  The destination computer must have the BizTalk Server runtime installed and the necessary BizTalk assemblies deployed and installed in the global assembly cache.  
  
2.  Run the .MSI file to install the Web service and follow the setup wizard prompts.  
  
    > [!IMPORTANT]
    >  Remove the "_Setup" suffix when the wizard prompts you for the virtual directory.Removing the suffix ensures that the receive location addresses match the Web service .asmx files.  
  
3.  Verify that the security settings for the virtual directory are correct for authorization.  
  
## See Also  
 [Deploying Published Web Services on a Non-Visual Studio Computer](../core/deploying-published-web-services-on-a-non-visual-studio-computer.md)