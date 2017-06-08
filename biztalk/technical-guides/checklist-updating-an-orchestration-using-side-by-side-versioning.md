---
title: "Checklist: Updating an Orchestration Using Side-by-Side Versioning | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97f66987-0269-4dfe-a648-7b68412e86fe
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Updating an Orchestration Using Side-by-Side Versioning
Changes to orchestrations can be more involved than changes to other artifacts, such as maps. If you have short-lived orchestrations, then a simple update may be sufficient. But if you have long-running orchestrations or cannot terminate existing instances, then side-by-side versioning will be your only option.  
  
 When an orchestration handles long-running transactions, you cannot change to the updated version of the orchestration immediately. You must allow the original version to finish processing its messages so that they are not lost. To accomplish this, you deploy the updated orchestration into the same application as the original one. You then stop the original version and start the updated version so that it receives all new messages while the previous version continues to process any in-flight messages. After the original orchestration has finished processing all of its messages, you undeploy it from the BizTalk application in which it was deployed.  
  
|Steps|Reference|  
|-----------|---------------|  
|After making the necessary changes to the orchestration, increment the assembly version number.|[How to Update an Assembly](../technical-guides/how-to-update-an-assembly.md)|  
|Deploy the assembly from Visual Studio into a BizTalk application, and then test the assembly. **Note:**  Make sure you select the deployment option to install the assembly in the GAC.|[Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154719) (http://go.microsoft.com/fwlink/?LinkID=154719).|  
|Export the assembly from the application in your test environment into an .msi file.|[How to Export an Application to an .msi File](../technical-guides/how-to-export-an-application-to-an-msi-file.md)|  
|Import the .msi file into the BizTalk application in your production environment that contains the orchestration that you want to update. **Note:**  You can use the following steps for testing the assembly as well as deploying it into your production environment.|[How to Import an Application from an .msi File](../technical-guides/how-to-import-an-application-from-an-msi-file.md)|  
|Bind the updated orchestration using the same bindings as the original orchestration.|[How to Configure Bindings for an Orchestration](http://go.microsoft.com/fwlink/?LinkId=154850) (http://go.microsoft.com/fwlink/?LinkId=154850).|  
|Unenlist the original orchestration, and then start the updated orchestration. **Note:**  To avoid any dropped messages, you should do this programmatically.|For more information about deploying the orchestration programmatically, see [Deploying and Starting a New Version of an Orchestration Programmatically](http://go.microsoft.com/fwlink/?LinkId=154851) (http://go.microsoft.com/fwlink/?LinkId=154851).<br /><br /> For more information about deploying the orchestration manually, see the following in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help:<br /><br /> -   [How to Unenlist an Orchestration](http://go.microsoft.com/fwlink/?LinkId=154852) (http://go.microsoft.com/fwlink/?LinkId=154852).<br />-   [How to Enlist an Orchestration](http://go.microsoft.com/fwlink/?LinkId=154853) (http://go.microsoft.com/fwlink/?LinkId=154853).<br />-   [How to Start an Orchestration](http://go.microsoft.com/fwlink/?LinkId=154854) (http://go.microsoft.com/fwlink/?LinkId=154854).|  
|Monitor the system for instances of the original orchestration version using the Group Hub page query view.|[How to View Instance Information for an Orchestration](http://go.microsoft.com/fwlink/?LinkId=154855) (http://go.microsoft.com/fwlink/?LinkId=154855).|  
|When all of its active, dehydrated, and suspended instances are complete, undeploy the original orchestration from the application.|[How to Remove an Orchestration from an Application](http://go.microsoft.com/fwlink/?LinkId=154856) (http://go.microsoft.com/fwlink/?LinkId=154856).|  
|Optionally uninstall the original assembly version from the GAC on each computer running the application.|[How to Uninstall an Assembly from the GAC](http://go.microsoft.com/fwlink/?LinkId=154857) (http://go.microsoft.com/fwlink/?LinkId=154857).|  
  
## Binding to Receive Ports and Locations  
 If you want to create new receive ports and locations for the new version of the orchestration, simply binding to the new ports and enlisting/starting the new artifacts will typically be sufficient. Creating new receive locations and ports is usually the preferred approach, especially if your scenario uses long-running orchestrations where a number of correlating receives still need to be processed. In this case, you may not be able to reuse existing receive ports or perform unenlistment. If you create new ports, be sure that it is possible for your backend and partner systems to handle this change. If not, you will have to wait for all long-running instances to culminate before upgrading.  
  
 If you want to use existing ports, do the following:  
  
1.  Bind the new version of the orchestration to existing ports.  
  
2.  Unenlist (but do not stop) the old orchestration version.  
  
3.  Enlist and start the new orchestration version.  
  
    > [!NOTE]  
    >  You can use a script to do steps 2 and 3 in one transaction, so that messages will not be missing subscriptions between manual clicking.