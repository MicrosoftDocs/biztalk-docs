---
title: "Deployment Limitations1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deployment, limitations"
ms.assetid: a984ccce-37b2-4738-b652-7232a18e0510
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deployment Limitations
The Transport Adapter password is stored as stars (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Server, and it passes to the management component in the same format. Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.  
  
 This is a known limitation. When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time that you use the file to import the binding information, you must enter the passwords by using transport property pages user interface. Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully finishes.  
  
> [!NOTE]
>  When importing an .msi file in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message. A supported hotfix is available from Microsoft along with a full description of the error at [http://go.microsoft.com/fwlink/?LinkID=196087](http://go.microsoft.com/fwlink/?LinkID=196087).  
  
## Password Limitation Workaround  
 To work around this password limitation, you can use one of the following methods:  
  
-   Edit the binding file before importing by replacing the stars with plain text.  
  
> [!CAUTION]
>  This is not recommended for security reasons.  
  
-   Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page in the BizTalk Server Administration Console after importing the binding file.  
  
> [!NOTE]
>  This work-around can be used only if Visual Studio is installed on the target computer, or if you develop a custom tool.  
  
-   Verify the Logical system and the Transmit and Receive services.  
  
## See Also  
 [Deploying Ports and Assemblies](../core/deploying-ports-and-assemblies2.md)