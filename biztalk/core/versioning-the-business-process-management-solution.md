---
title: "Versioning the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "versioning, process management solutions"
  - "process management solution tutorial, modifying"
  - "process management solution tutorial, versioning"
  - "processing, stages"
  - "process management solution tutorial, processing stages"
ms.assetid: 501b2162-821f-44e1-87c0-8628cc5bd9c3
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Versioning the Business Process Management Solution
The Business Process Management solution is designed so that you can replace stages if necessary. The design also provides for an easier method of versioning schemas.  
  
 For information about dividing a business process into stages, see [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
> [!NOTE]
>  Elements of the solution are highly dependent on the message structures. Changing message structures requires substantial changes to the orchestrations.  
  
 For general directions about updating assemblies in a deployed solution and guidelines for writing scripts to handle the update, see [Updating BizTalk Applications](../core/updating-biztalk-applications.md).  
  
## Adding, Replacing, or Removing Stages  
 The order processing stage orchestrations contain two kinds of code: code that implements the business process and code that provides the infrastructure so that it can operate in the solution. In both of the stage orchestrations, **CableOrder1** and **CableOrder2**, the business process code is inside a group shape labeled "Business Processing."  
  
 The easiest way to create a new stage is to copy one of the stages, replace the code in the "Business Processing" group with your code, and leave the infrastructure code intact.  
  
> [!NOTE]
>  The **CableOrder2** orchestration has two "Business Processing" groups, the second around the Update History Send shape. The Send shape is part of an efficient send scope. (For more information, see "Improving Performance with Nested Scopes" in [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).) Because a Group shape cannot overlap part of a scope shape, the second group is labeled to indicate it is part of the business process code.  
  
 You must set the filter expression on the new orchestration to its number in the sequence. The **OrderManager** assumes stage numbers begin with one and increase by one for each following stage (1, 2, 3 …). To filter for a third stage, you would set the filter expression to the following:  
  
 `(Microsoft.Samples.BizTalk.SouthridgeVidoe.Schemas.Stage == 3)`  
  
 The solution uses the BAM API to track events in the solution, including the order processing stages. The first stage starts the BAM activity; the final stage ends it. If there exceptions, the handlers in the solution end the BAM activities involved. BAM effectively re-assembles the discontinuous operations into a continuous view for monitoring.  
  
## Changing Configuration  
 If your changes increase or decrease the number of stages, you must change the configuration information stored in the Enterprise Single Sign-On (SSO) secret store.  
  
 If you haven't deployed the application, you can modify the configuration setting for **TotalStages** in the CreateSouthridgeVideoApplication.cmd script file. The value will change when the script is run during deployment.  
  
 If you have already deployed the application, you can change value by running a command line utility, BTSScnSSOApplicationConfig, in the SDK\Common\SsoApplicationConfig folder. To set the total number of stages to three, you'd use the following command line:  
  
 `BTSScnSSOApplicationConfig -set SouthRidgeVideo.CableOrder ConfigProperties TotalStages 3`  
  
 Because the solution caches the configuration values, you must wait until the  refresh interval passes for the new value to take effect.  
  
## Versioning Schemas  
 BizTalk takes a schema from the most recent version of the assembly containing it. This means that if you create a new version of a schema it completely replaces all previous versions of the schema. This works well when transactions are short-lived. However, transactions in the Business Process Management solution are long-lived: an order may take up to a year to complete.  
  
 To allow for the possibility of using multiple versions of a schema being in use, each schema in the solution includes a version number in its namespace. For example, the namespace for the Order schema is as follows:  
  
```  
http://Microsoft.Samples.BizTalk.SouthridgeVideo.Schemas.Order.v1  
```  
  
 Because the namespace identifies the schema and inclusion of the version number makes the namespace unique to the schema, the new schema will be distinct from the older version. Thus, a new schema can be used without supplanting the old schema.  
  
## See Also  
 [Developing a Business Process Management Solution](../core/developing-a-business-process-management-solution.md)