---
description: "Learn more about: Install the Dynamic Resolution Sample Using the Install Scripts"
title: "Install the Dynamic Resolution Sample Using the Install Scripts"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: install-set-up-deploy
---
# Install the Dynamic Resolution Sample Using the Install Scripts
This section describes how you can install the Dynamic Resolution sample from the install scripts provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 **To install the Dynamic Resolution sample from the install scripts**  
  
1.  If you want to execute one-way messaging examples that use FTP, create the following FTP site:  
  
    -   FTP Virtual Directory name: Out  
  
    -   Location: \Source\Samples\DynamicResolution\Test\FTP\Out  
  
    -   Permissions: Read and Write  
  
    -   Ensure the BizTalk Application Users group has full access permission for this location  
  
2.  If you want to execute two-way messaging examples that use MQSeries, use WebSphere Explorer to create the following:  
  
    -   A queue manager with the name ESB.DEP.Sample.QueueManager  
  
    -   A queue named TEST.OUT within the ESB.DEP.Sample.QueueManager  
  
3.  On the **Start** menu, click **Run**.  
  
4.  In the **Run** dialog box, type **cmd**, and then press ENTER to open the command prompt.  
  
5.  Run the following command, replacing the \<path\> parameter with the full path to the .cmd file you want to install (the default path in this release is \Source\Samples\DynamicResolution\Install\Scripts\\):  
  
    ```  
    <path>\Setup_bin.cmd  
    ```
