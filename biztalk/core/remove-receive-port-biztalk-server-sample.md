---
description: "Learn more about: Remove Receive Port (BizTalk Server Sample)"
title: "Remove Receive Port (BizTalk Server Sample)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Remove Receive Port (BizTalk Server Sample)
The Remove Receive Port sample demonstrates how to remove one or more receive ports.

> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.

## What This Sample Does
 The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:

-   Given a receive port name, query for a list of matching receive ports.

    > [!NOTE]
    >  Generally, there will only be one receive port that matches a given name.

-   Remove those receive ports.

-   Handle any errors such that meaningful information is returned to the user.

## Where to Find This Sample
 The samples are located in the following SDK location:

 \<*Samples Path*\>\Admin\WMI\Remove Receive Port\

 The following table shows the files in this sample and describes their purpose.

|File(s)|Description|
|---------------|-----------------|
|In the \VBScript folder:<br /><br /> RemoveReceivePort.vbs|VBScript file that takes a parameter that specifies one or more receive ports to remove.|

## Building and Initializing This Sample
 The Remove Receive Port sample consists of a single VBScript file that you do not need to build or initialize.

## Running This Sample

#### To run this sample

1.  In a command window, navigate to the following folder:

     \<*Samples Path*\>\Admin\WMI\Remove Receive Port\VBScript\

2.  Run the file RemoveReceivePort.vbs using the cscript program, passing the following command-line argument:

     **\<**
     ***ReceivePortName* \>**. The name of the receive port(s) to remove. If the receive port name contains spaces, enclose the name in quotes.

     For example:

    ```
    cscript RemoveReceivePort.vbs "My Business Receive Port"
    ```

## Comments
 All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.

 The script file RemoveReceivePort.vbs contains detailed comments with further explanation about the operations that it performs. For more information, see [Windows Management Instrumentation](/windows/win32/wmisdk/wmi-start-page).

## See Also
 [Admin-WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md)
