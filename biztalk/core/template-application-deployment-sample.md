---
title: "Template (Application Deployment Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, examples"
  - "scripts, deploying"
  - "deploying, scripts"
  - "examples, deploying"
ms.assetid: 7e77ff8e-b2bc-4d38-b5fd-329d6d54221f
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Template (Application Deployment Sample)
This topic describes how to use the Template sample for application deployment.  
  
 You can create and use two types of deployment scripts to customize BizTalk application deployment: pre-processing scripts and post-processing scripts. Pre-processing scripts are invoked before application installation and import begins and after uninstallation completes. Post-processing scripts are invoked after application installation and import completes and before uninstallation begins.  
  
 You can write pre- and post- processing scripts so that they are invoked for each of these operations. Alternatively, you can configure scripts to execute after only one of them. For more information about writing scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
 This topic demonstrates how to write and deploy a script so that it is invoked before or after only one operation. You do this by writing a script that checks the values of three environment variables to determine the operation in the context of which it is being called. Based on this context, the script either continues or discontinues execution.  
  
 This topic describes how to take the following steps:  
  
1.  Set the log file location, so that you can generate a log file of the script operations.  
  
    > [!NOTE]
    >  As a best practice, you should always generate a log file so that you can verify script operations and troubleshoot any problems.  
  
2.  Create a new BizTalk application and add the sample scripts to it.  
  
3.  Export an .msi file containing the application artifacts.  
  
4.  Delete the application from the BizTalk group, so that you can import the .msi file back into the same group as well as install it from the .msi file.  
  
5.  Import the application, and check the log file to see that the import operation was logged.  
  
6.  Install the application, and check the log file to see that the installation log was appended to the log file.  
  
7.  View the log files and note what operations the scripts performed and when they were performed.  
  
## What This Sample Does  
 Two .bat files provided for this sample contain the values of the environment variables for import, installation, and uninstallation. SamplePreProcessing.bat contains variables for a pre-processing script. SamplePostProcessing.bat contains variables for a post-processing script. The files also demonstrate how to log messages from scripts. You can copy the relevant sections of these files into your scripts.  
  
> [!IMPORTANT]
>  Some of the comments within the script files are incorrect, as follows:  
>   
>  In SamplePreProcessing.bat, the script comment, “Pre uninstall part of the script called for an existing application” should read "Post uninstall part of the script called for an existing application."  
>   
>  In SamplePostProcessing.bat, the script comment, “Post uninstall part of the script called for an existing application” should read "Pre uninstall part of the script called for an existing application."  
  
## Where to Find This Sample  
 The sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder, as follows:  
  
 *\<Samples Path\>*\Application Deployment\Template  
  
 As previously mentioned, the sample includes the following two files:  
  
-   SamplePreProcessing.bat  
  
-   SamplePostProcessing.bat  
  
## How to Use This Sample  
 To run the sample, take the following steps.  
  
### To set the logging location  
  
-   Open both the script samples and change the LogFile variable to point to the location where the log files are to be written. You must provide the full path including the file name. If it includes spaces, you must enclose the path in double quotation marks (").  
  
     Example:  
  
     set LogFile="*\<Samples Path\>*\ApplicationDeployment\Templates\SampleLogOut.txt"  
  
### To create a new application  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and expand the BizTalk group.  
  
3. Right-click **Applications** and then click **New**.  
  
4. In **Application name**, type `SamplesTemplate`, and then click **OK**.  
  
### To add the scripts to the application  
  
1.  Expand the folder of the SamplesTemplate application that you just created and right-click **Resources** in the left pane.  
  
2.  Point to **Add** and click **Pre-processing Scripts**.  
  
3.  Click **Add** and browse to SamplePreProcessing.bat.  
  
4.  Select the file and click **Open**.  
  
5.  In **File type**, click **System.BizTalk:PreprocessingScript**, and then click **OK**.  
  
     SamplePreProcessing.bat is added to the application and is displayed in the Resources folder of the application.  
  
6.  Right-click Resources again, point to **Add**, and then click **Post-processing Scripts**.  
  
7.  Click **Add** and browse to SamplePostProcessing.bat.  
  
8.  Select the file and click **Open**.  
  
9. In **File type**, click **System.BizTalk:PostprocessingScript**, and then click **OK**.  
  
     SamplePostProcessing.bat is added to the application and is displayed in the Resources folder of the application.  
  
### To export an .msi file  
  
1.  In the BizTalk Server Administration console, right-click the SamplesTemplate application, point to **Export**, and then click **MSI file**.  
  
2.  On the Welcome to the Export Wizard page, click **Next**.  
  
3.  On the Select Resources page, click **Next**.  
  
4.  On the Specify IIS Hosts page, click **Next**.  
  
5.  On the Dependencies page, click **Next**.  
  
6.  On the Destination page, in **Destination application name**, type the application name.  
  
7.  In **MSI file to generate**, type the full path for the MSI file, and then click **Export**. Example: C:\MSI\SamplesTemplate.msi  
  
8.  On the Summary page, click **Finish**.  
  
### Delete the application  
  
-   In the BizTalk Server Administration console, right-click the SamplesTemplate application, and then click **Delete**.  
  
### To import the .msi file  
  
1.  In the BizTalk Server Administration console, right-click **Applications**, point to **Import**, and then click **MSI file**.  
  
2.  On the Welcome to the Import Wizard page, in **MSI file to import**, type the path of the .msi file that you previously exported, and then click **Next**. If necessary, you can browse for the MSI file by clicking the **(….)** button.  
  
3.  On the Application Settings page, in the **Application name** drop-down list, select the application name.  
  
4.  In **Available applications to add references to**, select the applications to which to add references, if any, and then click **Next**.  
  
5.  On the Application Target Environment Settings page, click **Next**.  
  
    > [!NOTE]
    >  You do not need to specify a target environment for the purposes of this sample. For background information on this feature, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md). For instructions on adding binding files, see [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md).  
  
6.  On the Import Summary page, confirm that the summary information is correct, and then click **Import**.  
  
7.  On the Results page, click **Finish**.  
  
8.  Open the log file that was created when the scripts executed, and verify that import operation was logged.  
  
### To install the application  
  
1.  Double-click the .msi file and run the Installation Wizard.  
  
2.  Open the log file and verify that installation operation was added to the logging information.  
  
### To verify that the scripts functioned correctly  
  
-   Open the log files and verify that they executed during the specified operations.  
  
## See Also  
 [Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md)   
 [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md)