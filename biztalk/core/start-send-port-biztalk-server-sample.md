---
title: "Start Send Port (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send ports, examples"
  - "examples, send ports"
  - "send ports, starting"
ms.assetid: 84e54c9e-e9e8-4bb2-a191-20c29e127dae
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Start Send Port (BizTalk Server Sample)
The Start Send Port sample demonstrates how to start a send port and optionally set the Primary Transport Address when using the FILE adapter.  
  
> [!WARNING]
>  Deployment scripts should be removed after deployment if not needed. Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.  
  
## What This Sample Does  
 The Visual Basic Scripting Edition (VBScript) script in the script file that constitutes this sample shows how to perform the following operations using the BizTalk Server WMI provider:  
  
-   Given a send port name, query for a list of matching send ports.  
  
    > [!NOTE]
    >  Generally, there will only be one send port that matches a given name.  
  
-   Set the Primary Transport Address for those send ports (relative to the installation path).  
  
-   Start those send ports.  
  
## Where to Find This Sample  
 The sample files are located in the following SDK location:  
  
 \<*Samples Path*>\Admin\WMI\Start Send Port\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the \VBScript folder:<br /><br /> StartSendPort.vbs|VBScript file that takes parameters that specify a send port to start, and optionally, a new value for the Primary Transport Address associated with that port.|  
  
## Building and Initializing This Sample  
 The Start Send Port sample consists of a single VBScript file that you do not need to build or initialize.  
  
## Running This Sample  
  
#### To run this sample  
  
1.  In a command window, navigate to the following folder:  
  
     \<*Samples Path*>\Admin\WMI\Start Send Port\VBScript\  
  
2.  Run the file StartSendPort.vbs using the cscript program, passing the following command-line arguments, the second of which is optional:  
  
    -   **\<**   
         ***SendPortName* >.** The name of the send port to start. If the send port name contains spaces, enclose the name in quotes.  
  
    -   **\<**   
         ***PrimaryTransportAddress* >.** The Primary Transport Address, relative to the product installation location, that you can change by specifying this argument. If the primary adapter address contains spaces, enclose the name in quotes.  
  
         For example:  
  
        ```  
        cscript StartSendPort.vbs "My Business Send Port" SDK\Samples\HelloWorld\Out\%MessageID%.xml  
        ```  
  
## Comments  
 All tasks that you can perform in the BizTalk Server Administration console can also be performed by using script that accesses the Windows WMI object model.  
  
 The script file StartSendPort.vbs contains detailed comments with further explanation about the operations that it performs. For more information, see Windows Management Instrumentation at [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## See Also  
 [Admin-WMI (BizTalk Server Samples Folder)](../core/admin-wmi-biztalk-server-samples-folder.md)