---
title: "Deployment Limitations3 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "passwords, deployment limitations"
  - "deployment, password limitations"
  - "transport adapter password"
ms.assetid: 79cd330f-ecc5-430e-9d79-608593d873cb
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deployment Limitations
The Transport Adapter password is stored as stars (******) in the binding file that is exported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format.  
  
 When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface. Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation finishes.  
  
> [!NOTE]
>  When importing an .msi file in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message. A supported hotfix is available from Microsoft along with a full description of the error at [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).  
  
## Password Limitation Workaround  
 To work around this password limitation, you can use one of the following methods:  
  
-   Edit the binding file before importing by replacing the stars with plain text.  
  
    > [!CAUTION]
    >  This practice is not recommended for security reasons.  
  
-   Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.  
  
    > [!NOTE]
    >  This work-around can be used only if Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] is installed on the target computer, or if you develop a custom tool.  
  
 -or-  
  
-   Use Enterprise Single Sign-On (SSO) instead of using passwords.  
  
     Using the SSO option requires an import of the binding file.  
  
 Verify the logical system and the Transmit and Receive services.  
  
## See Also  
 [Deploying Ports and Assemblies](../core/deploying-ports-and-assemblies5.md)