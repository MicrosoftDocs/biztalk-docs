---
description: "Learn more about: Remove Send Port (BizTalk Server Sample)"
title: "Remove Send Port (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "send ports, examples"
  - "examples, send ports"
  - "send ports, deleting"
  - "deleting, send ports"
ms.assetid: e6643525-fa9f-4d39-880f-314749a68471
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Remove Send Port (BizTalk Server Sample)
The Remove Send Port sample demonstrates how to unenlist and remove one or more send ports.

> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.

## What This Sample Does
 The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:

-   Given a send port name, query for a list of matching send ports.

    > [!NOTE]
    >  Generally, there will only be one send port that matches a given name.

-   Unenlist those send ports.

-   Delete those send ports.

-   Handle any errors such that meaningful information is returned to the user.

## Where to Find This Sample
 The sample is located in the following SDK location:

 \<*Samples Path*\>\Admin\WMI\Remove Send Port\

 The following table shows the files in this sample and describes their purpose.

|File(s)|Description|
|---------------|-----------------|
|In the \VBScript folder:<br /><br /> RemoveSendPort.vbs|VBScript file that takes a parameter that specifies one or more send ports to unenlist and remove.|

## Building and Initializing This Sample
 The Remove Send Port sample consists of a single VBScript file that you not need to build or initialize.

## Running This Sample

#### To run the Remove Send Port sample

1.  In a command window, navigate to the following folder:

     \<*Samples Path*\>\Admin\WMI\Remove Receive Port\VBScript\

2.  Run the file RemoveSendPort.vbs using the cscript program, passing the following command-line argument:

     **\<**
     ***SendPortName* \>.** The name of the send port(s) to remove. If the send port name contains spaces, enclose the name in quotes.

     For example:

    ```
    cscript RemoveSendPort.vbs "My Business Send Port"
    ```

## Comments
 All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.

 The script file RemoveSendPort.vbs contains detailed comments with further explanation about the operations that it performs. For more information, see [Windows Management Instrumentation](/windows/win32/wmisdk/wmi-start-page).

## See Also
 [Admin-WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md)
