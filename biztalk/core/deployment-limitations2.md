---
title: "Deployment Limitations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deployment, limitations"
  - "passwords, adapter limitations"
ms.assetid: 9db2ca70-5db2-4b14-a898-13049737c188
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deployment Limitations
The Transport Adapter password is stored as asterisks (\*\*\*\*\*\*) in the binding file that is exported by BizTalk Deployment Wizard, and is passed to the management component in the same format. Edit the binding file before importing by replacing the asterisks with random alphanumeric values (that is, not the correct password). Then enter the correct password using the **Transport Properties** page after importing the binding file.  
  
 When you export binding information, the resultant binding file does not contain any of the passwords that were used by transport adapters in receive locations/send ports. This prevents password information from appearing in clear text. The next time you use the file to import the binding information, you must enter the passwords by using transport property pages user interface. Alternatively, you can temporarily modify the binding file before importing by typing the passwords into it. In this case, you must delete the passwords from the binding file after the import operation successfully completes.  
  
> [!NOTE]
>  When importing an .msi file into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application containing binding information for any of the Enterprise adapters, you may receive an import error message. A supported hotfix is available from Microsoft along with a full description of the error at [http://support.microsoft.com/kb/923733/en-us](http://support.microsoft.com/kb/923733/en-us).  
  
## Password Limitation Workaround  
 Use one of the following as a work-around for the password limitation.  
  
#### To work around the password limitation  
  
1.  Edit the binding file before importing by replacing the stars with plain text.  
  
    > [!CAUTION]
    >  This is not recommended for security reasons.  
  
2.  Edit the binding file before importing by replacing the stars with some junk value (that is, not the correct password). Enter the correct password using the **Transport Properties** page after importing the binding file.  
  
    > [!NOTE]
    >  This work-around can be used only if Microsoft Visual Studio is installed on the target computer or by developing a custom tool.  
  
 **-OR-**  
  
#### To work around the password limitation  
  
1.  Use Enterprise Single Sign-On instead of using passwords.  
  
     Using the SSO option requires no extra work; only an import of the binding file.  
  
2.  Verify the Logical system and the Transmit and Receive services.  
  
## See Also  
 [How to Set JD Edwards OneWorld Transport Properties](../core/how-to-set-jd-edwards-oneworld-transport-properties.md)   
 [Deploying Ports and Assemblies](../core/deploying-ports-and-assemblies4.md)