---
title: "How to Test and Modify a Transaction Integrator Application1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed25a406-5c45-4c57-b341-5ac5bd1dab18
caps.latest.revision: 4
---
# How to Test and Modify a Transaction Integrator Application
After you have finished coding your application, you may test and modify your application. During this process, you may need to undeploy and modify the host file interface.  
  
### To test and modify your TI application  
  
1.  Before compiling and executing your application, ensure that the host file interface is deployed.  
  
2.  Execute your application and test as you would any other application.  
  
3.  To undeploy a host file interface, right-click the name of the .dll that contains the interface and select **UnDeploy**.  
  
4.  Make modifications to the interface using HIS Designer, and then save your work.  
  
5.  Once you are finished making changes, you can deploy the interface again by clicking on the name of the .dll in HIS Designer and selecting **Deploy**.  
  
## See Also  
 [Creating an Application with Host Integration Server Designer](../core/creating-an-application-with-host-integration-server-designer2.md)