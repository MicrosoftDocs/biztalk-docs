---
description: "Learn more about: Set Send Handler Property (BizTalk Server Sample)"
title: "Set Send Handler Property (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "SMTP adapters, examples"
  - "examples, SMTP adapters"
  - "send handlers, properties"
ms.assetid: eb6ae2f2-528f-44ec-bca4-f37006893ff2
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Set Send Handler Property (BizTalk Server Sample)
The Set Send Handler Property sample demonstrates how to set the XML configuration information for a Simple Mail Transfer Protocol (SMTP) send handler.

> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.

## What This Sample Does
 The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:

-   Given a send handler name, query for a list of matching send handlers.

-   Set the XML configuration information for an SMTP send handler.

-   Handle any errors such that meaningful information is returned to the user.

## Where to Find This Sample
 The sample files are located in the following SDK location:

 \<*Samples Path*\>\Admin\WMI\Set Send Handler Property\

 The following table shows the files in this sample and describes their purpose.

|File(s)|Description|
|---------------|-----------------|
|In the \VBScript folder:<br /><br /> ConfigureSMTP.vbs|VBScript file that takes parameters that specify an SMTP send handler and a From e-mail address.|

## Building and Initializing This Sample
 The Set Send Handler Property sample consists of a single VBScript file that you do not need to build or initialize.

## Running This Sample

#### To run the Set Send Handler Property sample

1.  In a command window, navigate to the following folder:

     \<*Samples Path*\>\Admin\WMI\Set Send Handler Property\VBScript\

2.  Run the file ConfigureSMTP.vbs using the cscript program, passing the following command-line argument:

    -   **\<**
         ***SMTPServerName* \>.** The name of the SMTP server that will be used to send mail.

    -   **\<**
         ***FromEmailAddress* \>.** An e-mail address that will be used as the From address.

         For example:

        ```
        cscript ConfigureSMTP.vbs MyBusinessSMTPServer someone@example.com
        ```

## Comments
 All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.

 The script file ConfigureSMTP.vbs contains detailed comments with further explanation about the operations that it performs. For more information, see [Windows Management Instrumentation](/windows/win32/wmisdk/wmi-start-page).

## See Also
 [Admin-WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md)
