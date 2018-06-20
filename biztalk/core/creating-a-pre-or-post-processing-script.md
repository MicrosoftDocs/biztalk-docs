---
title: "Creating a Pre- or Post-processing Script | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scripts, post-processing"
  - "scripts, pre-processing"
  - "scripts, warnings"
  - "scripts, applications"
  - "applications, scripts"
  - "scripts, deploying"
  - "deploying, scripts"
ms.assetid: d5fbaec8-fbfe-4ceb-8ba8-0933baa37a1f
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a Pre- or Post-processing Script
You can create a script to perform actions when an application is deployed, and then define when it will run during the deployment process. You can include both installation and cleanup code in the same script, using environment variables to delimit the code. You can also pass command-line arguments into the script.  
  
> [!CAUTION]
>  You should always write scripts intended for production systems in silent mode. This is because a script waiting for user input will cause the BizTalk databases to become locked and inaccessible until the input is received.  
  
## Specifying when a script will run during deployment  
 You specify when a script will run when you add the script to an application by adding it as either a System.BizTalk:PreProcessingScript (pre-processing script) or a System.BizTalk:PostProcessingScript (post-processing script).  
  
 Pre- and post-processing scripts run as follows:  
  
- Pre-processing scripts run at the beginning of the import or installation process.  
  
- Post-processing scripts run at the end of the import or installation process.  
  
- During uninstallation, all scripts run in the opposite order that they run during installation. Therefore, post-processing scripts run at the beginning of uninstallation and pre-processing scripts at the end of uninstallation.  
  
- If an installation fails, scripts are called in reverse order with the appropriate rollback action.  
  
  Once invoked, a pre- or post-processing script determines which deployment state (install, import, delete, uninstall, import rollback, or install rollback) it is running in by checking the environment variables BTAD_ChangeRequestAction, BTAD_InstallMode, and BTAD_HostClass, as described in [How Environment Variables Indicate Deployment State](../core/how-environment-variables-indicate-deployment-state.md). For reference information about the variables, see [Pre- and Post-processing Script Environment Variables](../core/pre-and-post-processing-script-environment-variables.md).  
  
  For instructions on adding a script to an application, see [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).  
  
> [!NOTE]
>  If you want to include command-line arguments in a script, as discussed later in this topic, you must use the AddResource command to add the script.  
  
## Supported script file extensions  
 The following script file extensions are supported: .com, .exe, .bat, .cmd, .vbs, .vbe, .js, .jse, .wsf, and .wsh. This set of extensions is defined in the PATHEXT environment variable.  
  
## Logging errors  
 As a best practice, you should configure each script to log errors to a file. This is because Windows Installer does not log errors generated in the scripts. You should check these logs after the script runs for any errors that need to be addressed.  
  
 To help you determine when the error occurred, you can include the date and time in the log file.  
  
 Use the following code to specify a log file and then log an error to it.  
  
 `Set LogFile=<full path of log file>`  
  
 `…`  
  
 `echo %DATE% %TIME% <text> >> %LogFile%`  
  
 In the following example, when the public key token is not defined, an entry is made in the specified log file. In the log file, the date and time is written in the same line as the text, "Public key should be set in script."  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 You can also add the line `exit /b 1` to a script to generate an error code for Windows Installer, which will cause it to roll back.  
  
 In the following example, if the public key token has not been defined, the script will return an error to Windows Installer, and the installer will roll back.  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 `exit /b 1`  
  
## Including installation and cleanup code in the same script  
 Because scripts run in the opposite order during installation and uninstallation, you can include installation and cleanup code in the same script, inside a conditional statement. For example, you can place the installation code within a conditional statement that checks for the installation mode, as follows:  
  
```  
  
%BTAD_ChangeRequestAction%=Update AND %BTAD_InstallMode%=Install  
  
```  
  
 You can qualify cleanup code within a conditional statement that checks for the installation mode, as follows:  
  
```  
  
%BTAD_ChangeRequestAction%=Delete AND %BTAD_InstallMode%=Uninstall  
  
```  
  
## Passing in command-line arguments  
 You can pass command-line arguments into the script by specifying the following parameter when you use the BTSTask AddResource command to add the script to the application. When you do this, the arguments are passed to the script when the script is invoked.  
  
 **/Property:Args=**"*argument list*"  
  
> [!NOTE]
>  If you have multiple pre- or post-processing scripts in and application, they are run in no particular order.  
  
> [!IMPORTANT]
>  You should not use BTSTask commands in scripts, especially those that run during import, because scripts are not enlisted in the same transaction as an import.  
  
 For instructions on using the AddResource command to add a script to an application, see [AddResource Command: Preprocessing Script](../core/addresource-command-preprocessing-script.md). Also see [AddResource Command: Postprocessing Script](../core/addresource-command-postprocessing-script.md)  
  
## See Also  
 [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)   
 [Template (Application Deployment Sample)](../core/template-application-deployment-sample.md)