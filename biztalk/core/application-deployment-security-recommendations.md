---
description: "Learn more about: Application Deployment Security Recommendations"
title: "Application Deployment Security Recommendations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Application Deployment Security Recommendations
The following are guidelines for deploying BizTalk applications in your environment:  
  
-   All discretionary access control lists (DACLs) are removed from files and folders when an application is exported into an .msi file. After installing an application from the .msi file, you must reconfigure all security settings on the files and folders.  
  
-   For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file. After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function. You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location. For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md). See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md). For more information about binding files, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
-   Deploying or undeploying a property schema may expose sensitive data, and subsequently expose sensitive information during tracking. Whenever an assembly containing a property schema is deployed or undeployed, the event viewer logs an event in the Windows Application Event Log. You should check the event log for these messages to ensure that all assembly deployment activities are in line with your policies for any sensitive data.  
  
     The message generated to the Event Log for deployment is:  
  
     **The user "{1}" deployed the assembly "{0}" containing property schemas.**  
  
     The message generated to the Event Log for undeployment is:  
  
     **The user "{1}" undeployed the assembly "{0}" containing property schemas.**  
  
-   If the application includes a virtual directory, be aware that the security settings on the virtual directory are those in effect when the .msi file is generated during application export. If you are deploying an application into a production environment, before exporting the application, you should verify that the settings meet your security requirements.  
  
     If, however, you deploy an application that includes a virtual directory, and the virtual directory already exists in the destination environment, the security settings on the existing virtual directory will be in effect. They are not changed to match those on the virtual directory you are deploying. You should verify that the security settings on the existing virtual directory meet your requirements.  
  
    > [!CAUTION]
    >  If the virtual directory uses the HTTPS (Hypertext Transfer Protocol over Secure Socket Layer) protocol, its security settings are not preserved during export, and when it is imported, the virtual directory will inherit the security settings of the root. You should verify that the security settings meet your requirements.  
  
-   If the application pool specified for a Web service does not exist when you import an application, the default application pool is used. The security settings on the default application pool may not be appropriate for your requirements. We therefore recommend that you either create the application pool and configure the appropriate security settings before importing the application, or verify that the settings on the default application pool are appropriate.  
  
-   Ensure that you trust the source of the Windows Installer (.msi) files that you deploy to avoid security issues that can be created by malicious .msi file creators. For more information, see [Security and Windows Installer](../core/security-and-windows-installer.md).  
  
-   Ensure you have the permissions to deploy applications. For more information, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
-   Ensure that only BizTalk administrators have access to the assemblies, binding files, and policy files, as they may contain critical business data such as connectivity and configuration information. If you deploy applications through a network share, configure the discretionary access control list (DACL) on the network share so that only BizTalk administrators can view its contents. For more information about group and user accounts, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   When you perform deployment operations, BizTalk Server communicates with the BizTalk Management database. If a firewall exists between them, you must open the appropriate ports on the firewall between the processing, services, and data domains. For more information, see [Required Ports for BizTalk Server](../core/required-ports-for-biztalk-server.md).  
  
-   If you point to a remote location for an assembly, binding file, or other resource file that may contain sensitive data, you should consider network security between source computer and the computer from which you are running deployment. If the network between these two computers is not fully isolated from potential attackers, you should copy the target file to removable media and physically transport it to the computer where you run deployment.  
  
## See Also  
 [Security Considerations for Application Deployment](../core/security-considerations-for-application-deployment.md)
