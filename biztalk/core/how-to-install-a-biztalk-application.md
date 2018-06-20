---
title: "How to Install a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installing, requirements"
  - "installing, applications"
  - "installing, warnings"
  - "applications, installing"
ms.assetid: 99ee0b1a-d46a-4fb6-802b-6827dc740418
caps.latest.revision: 56
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Install a BizTalk Application
This topic describes how to install an application on the local computer by double-clicking the Windows Installer (.msi) file for the application in the Windows interface or by running msiexec from the command line. You can also start the Installation Wizard as the last step of the Import Wizard, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).  

> [!CAUTION]
>  If this application has already been installed on this computer, you will be given the option to repair the application. Repair is supported only when a single .msi has been installed for this application. If you have installed more than one .msi on this computer for this application, you should not select this option. This is because selecting Repair will undo any changes made by .msi files that were installed subsequent to this .msi file, which may cause your application to malfunction.  

 Before you can put an application into operation, you must install it on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers that will run it. Installing an application places its resources on the local file system. Depending on the application, its contents, and its configuration, installation may also do the following:  

- Add assemblies to the global assembly cache (GAC)  

- Install certificates and virtual directories  

- Add components to the Windows registry.  

- Run pre- or post-processing scripts, if they are present in the .msi file.  

  For background information, see [What Happens to Artifacts During Installation and Uninstallation](../core/what-happens-to-artifacts-during-installation-and-uninstallation.md).  

## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that has Write permissions on the local file system. Depending on the items included in the application, you may also need Write permissions on the Windows Registry, GAC, the certificate store, and Internet Information Services. The Administrators account on the local computer has these permissions. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  

## Considerations for installing an application  
 When installing an application, the following considerations may apply:  

- **You must also install any applications on which this application has a dependency.** When you install an application that has a dependency on an artifact, such as a BizTalk assembly, which is contained in another application, you must also install the application that contains the artifact. You must do this before you can run the application. For example, if Application A depends on an assembly in Application B, you must also install Application B. Then you can install Application A. For background information, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).  

- **You should stop an application that you are updating.** If you are performing the installation to update an artifact in the application, you do not need to stop the application unless the update includes one or more assemblies that have the same version as existing assemblies. In this case, you must stop the application before installing the update. We recommend, however, that you stop the application in all cases unless you know that the update will not interfere with the application as it runs. For more information, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).  

- **When you install multiple .msi files for the same application, there is only one entry made in Add or Remove Programs.** You might do this to update an existing application, for example. You can then use Add or Remove Programs (in Control Panel) to uninstall the application completely, including any updated items. Note that uninstalling an application by double-clicking the .msi file or using msiexec is not supported. For more information, see [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md).  

- **Certificates must be present on all computers that host send ports before an application can run.** The Other People Certificate store contains the certificates used by send ports.  

- **You can factor application artifacts into different .msi files for installation.** You do not need to install all application artifacts on each computer that will run the application. Instead, you can export subsets of application artifacts into different .msi files to install on different computers. For instructions, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  

- **If the application .msi file includes a virtual directory, Internet Information Services (IIS) must be running on the local computer.** If it does not, the installation will fail.  

- **If the application includes a virtual directory with the same name as one that already exists on the local computer, resources from the application are added to it.** Otherwise, the virtual directory is created. Any existing files that have the same name as added files will be overwritten. In addition, security settings for an existing virtual directory are not changed, and you should verify that they are sufficiently secure.  

- **Create application pools for virtual directories before installing an application.** If your application includes a virtual directory, and the application pool does not already exist in IIS, you should manually create the application pool before installation. This way, the virtual directory will be bound to the application pool during installation. If you do not create the application, the virtual directory will be bound to the default application pool on installation.  

- **Ensure that BTSHttpReceive.dll is registered as a Handler Mapping with Internet Information Services (IIS) 7.0.** You must do this if your application includes a virtual directory  in order for the HTTP receive location to work.  

- **You may encounter issues when installing an application that includes 64-bit artifacts on a 32-bit computer.** For more information, see [How to Add a 64-Bit Artifact to an Application](../core/how-to-add-a-64-bit-artifact-to-an-application.md).  

- **You may encounter issues if the target directory length exceeds 260 characters.** If the number of characters in the target directory that is specified during the installation of an MSI package exceeds 260 characters then the installation will fail. To resolve this problem, ensure that the number of characters specified for the target directory does not exceed 260 characters.  

- **You should not relocate an installation folder.** Once you install an application, you should not relocate the installation folder or the files it contains. If you do, and then later attempt to remove (uninstall) the application, the removal operation may fail. In particular, the application installation folder contains files generated by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that are necessary to perform the removal. You should not rename, move, or remove these files. The files are:  

  -   ApplicationDefinition.adf  

  -   Microsoft.BizTalk.CustomInstaller.dll  

  -   Microsoft.BizTalk.CustomInstaller.InstallState  

> [!NOTE]
>  If you cancel the installation operation before it completes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will roll back the installation, except for any actions that were taken by pre- or post-processing scripts before the operation was canceled.  
> 
> [!IMPORTANT]
>  Before installing any application, be sure that you have received the .msi file from a trusted source. A malicious user can include code in an .msi file that can have an undesirable affect on your system or network.  For more information, see [Security and Windows Installer](../core/security-and-windows-installer.md).  
> 
>  If the application includes a Web site or an orchestration that uses a Web service, be aware that the security settings on the virtual directory are those that are in effect when the .msi file is generated during application export, except in the case of an existing virtual directory, the existing settings are used. After installing the application, you should verify that the settings meet your security requirements.  
> 
>  Alldiscretionary access control lists (DACLs) are removed from files and folders when an application is exported. After installing an application on a host instance, you must reconfigure all security settings on the files and folders, including virtual directories.  

-   **You may need to change the Local path: designation of a virtual directory that is referenced by an HTTP receive location after it is created on the target computer.**  

     When the virtual directory is created on the target computer it will point to one of the following physical directories:  

     \<*installation drive*\>\Program Files\Microsoft BizTalk Server\HttpReceive  

     \- **or** –  

     \<*installation drive*\>\Program Files (x86)\Microsoft BizTalk Server\HttpReceive  

     If the BizTalk HTTP receive ISAPI extension BTSHTTPReceive.dll is not located in the specified directory or if the target computer is running a 64 bit operating system then you must change the Local path: designation of the virtual directory to point to the physical directory that contains the BizTalk HTTP receive ISAPI extension file. For example, if the target machine is running the 64 bit version of Windows Vista, then the Local path: designation of the virtual directory should be changed to \<installation drive\>\Program Files (x86)\Microsoft BizTalk Server\HttpReceive64.  

## To install a BizTalk application  

#### Using the Windows interface  

1. Copy the .msi file for the application to the local computer.  

2. If you are reinstalling or upgrading an existing BizTalk application, and the new installation includes an assembly that has the same version as one that already exists in the application, or interacts with an artifact that you are updating, ensure that the application is stopped by right-clicking the application folder and then clicking **Stop**.  

3. In Windows Explorer, double click the .msi file to start the Installation Wizard.  

4. On the **Select Installation Folder** page, in **Folder**, type the complete installation path for the BizTalk application. Example: C:\Program Files\Generated by BizTalk\MyApplication.  

5. Click **Next** four times, and then on the **Installation Complete** page, click **Close**.  

6. If multiple computers will be running the application, repeat the previous steps on each computer.  

    Once the application is installed on all computers that will run it, and the application has been imported into the BizTalk group, you can start the application from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console by right-clicking the application's folder and clicking **Start**. For complete instructions, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  

#### Using the command line  

1. Copy the .msi file for the application to the local computer.  

2. Click **Start**, click **Run**, type `cmd`, and then press ENTER.  

3. Navigate to the location where the .msi file is stored.  

4. Type the following command to install the application, providing the appropriate parameters and values, as shown in the following table:  

   > [!IMPORTANT]
   >  Only the parameters of msiexec displayed in the following table are supported.  

    **msiexec** [**/i**] *Package* [**/qn**] **TARGETDIR="**<em>value</em>**"**]  

    Example: **msiexec /i MyApplication.msi**  


   |           Parameter           |                                                                                                 Value                                                                                                 |
   |-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **/i**             |                                                                                       Installs the application.                                                                                       |
   |           *Package*           |                                                                              Name of the Windows Installer (.msi) file.                                                                               |
   |            **/qn**            |                                                                    Performs the installation without displaying a user interface.                                                                     |
   | **TARGETDIR="** *value* **"** | Specifies the application installation folder. This value is also set in the %BTAD_InstallDir% environment variable.<br /><br /> Example: TARGETDIR="C:\Programs\BizTalk Applications\My Application" |


5. If multiple computers will be running the application, repeat the previous steps on each computer.  

    Once the application is installed on all computers that will run it, you can start the application from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console by right-clicking the application's folder and clicking **Start**. For complete instructions, see [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  

## See Also  
 [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md)   
 [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)