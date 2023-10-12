---
description: "Learn more about: Install the JMS MQRFH2 Sample Using the Install Scripts"
title: "Install the JMS MQRFH2 Sample Using the Install Scripts"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Install the JMS MQRFH2 Sample Using the Install Scripts
This section describes how you can install the JMS MQRFH2 sample using the install scripts provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].  
  
 **To install the JMS MQRFH2 samples from the install scripts**  
  
1.  Using WebSphere Explorer, create a Queue Manager with the name **ESB.JMS.Sample.QueueManager**.  
  
2.  Using WebSphere Explorer, create the following four queues within **ESB.JMS.Sample.QueueManager:**  
  
    -   ESB.JMS.SAMPLE.DYNAMICQ1  
  
    -   ESB.JMS.SAMPLE.DYNAMICQ2  
  
    -   ESB.JMS.SAMPLE.REPLY  
  
    -   ESB.JMS.SAMPLE.SENDTOBIZTALK  
  
3.  On the **Start** menu, click **Run**.  
  
4.  In the **Run** dialog box, type **cmd**, and then press ENTER.  
  
5.  Run the following command, replacing the *\<path\>* parameter with the full path to the .cmd file you want to install (the default path in this release is \Source\Samples\JMS\Install\Scripts\\):  
  
    ```  
    <path>\Setup_bin.cmd  
    ```
