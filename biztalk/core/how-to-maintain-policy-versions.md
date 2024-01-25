---
description: "Learn more about: How to Maintain Policy Versions"
title: "How to Maintain Policy Versions"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Maintain Policy Versions
After you add rules to a version of your policy, you can save the version to the rule store for further development, or you can publish it to create a well-defined, immutable set of rules that can be deployed for use in a rule-based application.  
  
 This topic contains procedures for the following tasks:  
  
-   To create an empty new version of a policy  
  
-   To save a policy version  
  
-   To publish a policy version  
  
-   To create an updated version of a policy  
  
-   To update a policy to use an updated assembly  
  
### To create an empty new version of a policy  
  
-   Right-click the policy folder, and then click **Add New Version**.  
  
### To save a policy version  
  
-   Right-click the policy version, and then click **Save**.  
  
### To publish a policy version  
  
-   Right-click the policy version, and then click **Publish**.  
  
### To create an updated version of a policy  
  
1.  Right-click an existing policy version, and then click **Copy**.  
  
2.  Right-click the policy folder, and then click **Paste**.  
  
     A new version is created, with the same elements as the copied version.  
  
    > [!NOTE]
    >  If your policy uses a .NET assembly, and the assembly is updated, you should bind your policy to the newer version of the assembly.  
  
### To update a policy to use an updated assembly  
  
1.  Click **Start**, point to **Administrative Tools**, point to **.NET Framework Configuration**, and then click **Configured Assemblies**.  
  
2.  Go to properties for the target assembly and click the **Binding Policy** tab.  
  
3.  In the global assembly cache, change the version number to the newer version.  
  
    > [!NOTE]
    >  All assemblies used by policies should be added to the global assembly cache.
