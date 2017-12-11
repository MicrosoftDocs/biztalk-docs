---
title: "How to Deploy an Assembly for the Managed Data Provider for Host Files | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38bbb35b-6730-4efd-9930-c1fd3ceedb90
caps.latest.revision: 3
---
# How to Deploy an Assembly for the Managed Data Provider for Host Files
Once you have created the assembly that contains your code, you can deploy the assembly to your local computer. Deploying the assembly registers the assembly with Host Integration Server and Transaction Integrator, and loads the assembly into the appropriate location to be used. After you deploy the assembly, you can test the interfaces and the code that you wrote. You can then undeploy the assembly, modify the code, and redeploy as necessary.  
  
### To deploy and undeploy an assembly to your local machine  
  
1.  In HIS Designer, select the tab that has the name of the assembly to deploy.  
  
2.  In the **Properties** window, confirm that you have selected the remote environment that you want your assembly to communicate with.  
  
3.  In the HIS tree node, right-click the name of the assembly, and select **Deploy**.  
  
4.  Test your application as necessary.  
  
5.  When you are finished, you may undeploy your assembly by right-clicking the assembly name in HIS Designer, and selecting **UnDeploy**.  
  
## See Also  
 [Creating an Application for the BizTalk Adapter for Host Applications](../HIS2010/creating-an-application-for-the-biztalk-adapter-for-host-applications1.md)