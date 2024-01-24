---
description: "Learn more about: Deploying BRE Policies for Existing Messages"
title: "Deploying BRE Policies for Existing Messages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Deploying BRE Policies for Existing Messages
**To deploy the related business rules:**  
  
1.  Click **Start**, click **Programs**, click **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.  
  
2.  In BRE Deployment Utility, click **Browse**.  
  
3.  In the .NET Global Assembly Cache dialog box, select **SWIFT MX Schema**, and then click **OK**.  
  
4.  Click **Deploy**.  
  
     Based on the schemas deployed with that assembly, the deployment utility identifies the related rules and publishes them for use with the BRE. When complete, the BRE Deployment Utility displays the following message: "Deployment has completed. View the log file or Business Rules Composer for details."  
  
5.  Close the SWIFT BRE Deployment Utility dialog box.  
  
6.  In Windows Explorer, browse to *\<drive\>*:\Documents and Settings\All Users\Application Data to confirm that the log file BREDeploymentLog.txt appears in the folder.  
  
7.  Click **Start**, click **Run**, type **services.msc**, and then click **OK**. In the Services (Local) window, right-click **Rule Engine Update Service**, and then click **Restart**.
