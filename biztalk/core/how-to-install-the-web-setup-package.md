---
description: "Learn more about: How to Install the Web Setup Package"
title: "How to Install the Web Setup Package"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: install-set-up-deploy
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
