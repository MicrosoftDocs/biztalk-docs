---
title: "SelectiveBindingImport (Application Deployment Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "binding files, importing"
  - "examples, applications"
  - "binding files, examples"
  - "examples, importing"
  - "applications, binding files"
  - "applications, examples"
  - "applications, importing"
  - "deploying, scripts"
  - "examples, binding files"
ms.assetid: 963bfc80-8cc4-4d90-96b4-e85ae04405cf
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SelectiveBindingImport (Application Deployment Sample)
This topic explains how to use the SelectiveBindingImport sample. You can use this sample script to apply different bindings to an application when you import the application into different destination environments. You can use this approach when you want to import the bindings from binding files that are stored on a network share.  
  
> [!NOTE]
>  If you do not need to automatically import binding files from a network share during application import, you can add to the application different binding files that have different destination environments specified. When you import the application, you can specify the environment, and the bindings for that environment will be applied automatically. For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).  
  
 BizTalk applications are typically moved from development to testing to staging and then to production environments. The bindings used in different environments are typically different. Using this sample, you can apply bindings for different environments as follows:  
  
1.  Placing all the binding files that you want to use on a network share.  
  
2.  Adding a post-processing script to the application that will import from this location the correct binding file for the particular destination environment during application import. The script detects the environment by reading an environment variable named %ENVIRONMENT% that you set on the local computer,  
  
## What This Sample Does  
 This sample illustrates how to selectively import binding files from a network share by using a post-processing script contained in a BizTalk application .msi file.  
  
## Where to Find This Sample  
 You can find the following sample folders and files under *\<Samples Path\>*\Application Deployment\SelectiveBindingImport:  
  
-   Develop (Folder)  
  
    -   Dev.xml  
  
-   Production (Folder)  
  
    -   Production.xml  
  
-   Staging (Folder)  
  
    -   Staging.xml  
  
-   Test (Folder)  
  
    -   Test.xml  
  
-   SelectiveBindings.bat  
  
## How to Use This Sample  
 Use the following procedures to run this sample.  
  
### To run the sample  
  
1. Run **Build.Bat from the *\<Samples Path\>*\Application Deployment\CreateApp** directory. This creates the following files in the *\<Samples Path\>*\Application Deployment\CreateApp\Dlls folder: Schemas.dll, Maps.dll, and Orchestrations.dll.  
  
2. **Create the application.** In the BizTalk Server Administration console, create an application, as described in [How to Create an Application](../core/how-to-create-an-application.md).  
  
3. **Add to the application the .dll files created in the first step.** For instructions, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
4. **Create the ENVIRONMENT variable, as follows:**  
  
   1.  On the Start menu, right-click **My Computer** and click **Properties**.  
  
   2.  On the **Advanced** tab, click **Environment Variables**.  
  
   3.  In the **User variables** section, click **New**.  
  
   4.  In **Variable name**, type **ENVIRONMENT**.  
  
   5.  In **Variable value**, type on of the following values for the environment: **Develop**, **Production**, **Staging**, or **Test**. These values are case sensitive.  
  
5. Click **OK** three times.  
  
6. **Copy the binding files to a location on your file system.** Copy the binding .xml files from the Develop, Test, Staging, and Production folders to a location on your file system.  
  
7. **Edit the post-processing script.** Edit SelectiveBindings.bat as follows:  
  
   1.  **Specify the binding file location.** In the line containing BINDINGS_LOC, delete REM, and provide the path to the location where you copied the binding files.  
  
        Example:  
  
        BINDINGS_LOC=C:\MyBindings  
  
   2.  **Specify the application name.** In the line containing APPLICATION_NAME, delete REM, and provide the name of the application into which you want to import the bindings.  
  
        Example:  
  
        APPLICATION_Name=SelectiveBindingImport  
  
8. **Add the script to the application as a post-processing script.** For instructions, see [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).  
  
9. **Export the application.** For instructions, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).  
  
10. **Delete the application.** For instructions, see [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).  
  
11. **Import the application.** For instructions, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md). You do not need to specify a destination environment.  
  
12. **Verify that the right binding file was applied.** You can do this by checking the description field of the receive locations, as follows:  
  
    1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
    2. In the console tree, expand the BizTalk group, the BizTalk application, and the Receive Locations folder.  
  
    3. In the right pane, view the description of the receive locations.  
  
13. **Install the application.** For instructions, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).  
  
## See Also  
 [Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md)   
 [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md)