---
description: "Learn more about: Enable Receive Location (BizTalk Server Sample)"
title: "Enable Receive Location (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "receive locations, examples"
  - "receive locations, enabling"
  - "examples, receive locations"
ms.assetid: dd04b38a-634d-4c9a-b31a-2f226fa91d19
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enable Receive Location (BizTalk Server Sample)
The Enable Receive Location sample demonstrates how to enable a receive location and optionally set the Inbound Transport URL for that receive location.

> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.

## What This Sample Does
 The Microsoft Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:

-   Given a receive port name and receive location, query for a list of matching receive locations.

-   Set the Inbound Transport URL for a receive location (relative to the installation path).

-   Enable a receive location.

-   Handle any errors such that meaningful information is returned to the user.

## Where to Find This Sample
 The sample is located in the following SDK location:

 \<*Samples Path*\>\Admin\WMI\Enable Receive Location\

 The following table shows the files in this sample and describes their purpose.

|File(s)|Description|
|---------------|-----------------|
|In the \VBScript folder:<br /><br /> EnableRecLoc.vbs|VBScript file that takes parameters that specify a receive location to be enabled, and optionally, a new value for the Inbound Transport URL associated with that receive location.|

## Building and Initializing This Sample
 The Enable Receive Location sample consists of a single VBScript file that you do not need to build or initialize.

## Running This Sample

#### To run this sample

1.  In a command window, navigate to the following folder:

     \<*Samples Path*\>\Admin\WMI\Enable Receive Location\VBScript\

2.  Run the file EnableRecLoc.vbs using the cscript program, passing the following command-line arguments, of which the third one is optional:

    -   **\<**
         ***ReceivePortName* \>.** The name of the receive port that contains the receive location to be enabled. If the receive port name contains spaces, enclose the name in quotes.

    -   **\<**
         ***ReceiveLocationName* \>.** The name of the receive location within the specified receive port to be enabled. If the receive location name contains spaces, enclose the name in quotes.

    -   **\<**
         ***InboundTransportURI* \>.** A receive adapter URI, relative to the product installation location, that you can change by specifying this argument. If the inbound adapter URI contains spaces, enclose the URI in quotes.

         For example:

        ```
        cscript EnableRecLoc.vbs "My Business Receive Port" MyBusinessReceiveLocation
        ```

         -OR-

        ```
        cscript EnableRecLoc.vbs MyBusinessReceivePort "My Business Receive Location" SDK\Samples\HelloWorld\In\*.xml
        ```

## Comments
 All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.

 The script file EnableRecLoc.vbs contains detailed comments with further explanation about the operations that it performs.

 For more information, see Windows Management Instrumentation at [https://go.microsoft.com/fwlink/?LinkId=21102](https://go.microsoft.com/fwlink/?LinkId=21102).

## See Also
 [Admin-WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md)
