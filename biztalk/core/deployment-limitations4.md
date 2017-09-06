---
title: "Deployment Limitations4 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "passwords, deployment limitations"
  - "deployment, limitations"
ms.assetid: 1312627e-9de2-461e-a8c4-66a9d41bb714
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deployment Limitations
The Transport Adapter password is stored as stars (******) in the binding file that is exported by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and it passes to the management component in the same format. Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password).  
  
 When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface.  
  
 Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully completes.  
  
> [!NOTE]
>  When importing an .msi file in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message. A supported hotfix is available from Microsoft along with a full description of the error at [http://go.microsoft.com/fwlink/?LinkId=196087](http://go.microsoft.com/fwlink/?LinkId=196087).  
  
## Password Limitation Workaround  
 To work around the password limitation, you can do the following.  
  
#### To work around the password limitation  
  
1.  Use Enterprise Single Sign-On instead of using passwords. Using the SSO option requires no extra work; only an import of the binding file.  
  
2.  Verify the Logical system and the Transmit and Receive services.  
  
## See Also  
 [Deploying Ports and Assemblies](../core/deploying-ports-and-assemblies3.md)