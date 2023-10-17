---
title: "Manage Policies"
description: Quick links to import, publish, add, deploy, remove, or export a policy in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Manage policies

## Overview
The topics in this section provide instructions on using the BizTalk Server Administration console or the BTSTask command-line tool to manage policies. A policy is a logical grouping of business rules. For background information on policies, see [Policies](../core/policies.md).  
  
## Import, publish, deploy, and remove policies
 Solution developers can create and view policies by using the Business Rule Composer, as described in [Creating Business Rules Using the Business Rule Composer](../core/creating-business-rules-using-the-business-rule-composer.md). Developers and IT administrators can then perform the following tasks, which are described in the topics in this section, to deploy and manage policies in a BizTalk group and application:  
  
-   **Import the policy into a BizTalk group.** When you do this, the policy is added to the Rule Engine database for the group and displays in the BizTalk Server Administration console in the \<All Artifacts\> node for the BizTalk group. This does not put the policy into effect for any particular application. You must first publish the policy, add it to an application, and then deploy it, as described in other topics in this section. The Rule Engine database is a database that contains all of the policies in a BizTalk group.  
  
-   **Publish a policy.** This makes it available to use in a BizTalk application.  
  
-   **Add a policy to a BizTalk application.** This allows the application to use the policy, but does not put the policy into effect. The policy takes effect when it is deployed.  
  
    > [!IMPORTANT]
    >  If a policy is shared across two or more applications, you should create a separate application to contain the policy and then create references from the applications that use the policy to the application containing the policy. This is because if you stop an application that contains a policy, the policy is automatically undeployed and no longer functions for any of the applications that use it.  
  
-   **Deploy a policy.** Doing this puts it into operation. (This is similar to starting an orchestration.) You can deploy and undeploy a policy manually. In addition, when an application is started, its policies are automatically deployed, and when an application is stopped, its policies are automatically undeployed.  
  
    > [!NOTE]
    >  Once a policy is deployed, it can no longer be modified. If you want to modify a deployed policy, you must either undeploy it, or recreate it by using the Business Rule Composer and give it a new version number.  
  
-   **Remove a policy from a BizTalk application and the BizTalk group.** This undeploys the policy and removes it from the application as well as the Rule Engine database for the group.  
  
-   **Export the policy.** You can then import it into a different BizTalk group to use there.  
  
> [!NOTE]
>  You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks. For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Next steps
  
-   [Import a Policy](../core/how-to-import-a-policy.md)  
  
-   [Publish a Policy](../core/how-to-publish-a-policy.md)  
  
-   [Add a Policy to an Application](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [Deploy or Undeploy a Policy](../core/how-to-deploy-or-undeploy-a-policy.md)  
  
-   [Configure Tracking for a Policy](../core/how-to-configure-tracking-for-a-policy.md)  
  
-   [Remove a Policy from an Application and the BizTalk Group](../core/how-to-remove-a-policy-from-an-application-and-the-biztalk-group.md)  
  
-   [Export a Policy](../core/how-to-export-a-policy.md)