---
description: "Learn more about: Using Policy Explorer"
title: "Using Policy Explorer"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Using Policy Explorer
You can use the Policy Explorer to manage policies and rules in the rule store. You can create, modify, and delete policies and rules, and you can test, publish, deploy, and undeploy policies.  
  
 The following table describes the commands within the Policy Explorer that can be used in the process of developing new policies and rules.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add New Policy**|Create a new policy (rule set).|  
|**Add New Version**|Create a new empty version of the selected policy. You can copy rules from other versions and paste them into the new version.|  
|**Copy (Policy Version)**|Copy the selected policy version to the Clipboard.|  
|**Copy (Rule)**|Copy the selected rule to the Clipboard.|  
|**Cut (Rule)**|Copy the selected rule to the Clipboard and delete it.|  
|**Paste (Policy Version)**|Paste a policy version and its contents into a selected policy.|  
|**Paste (Rule)**|Paste a rule into the selected policy version.|  
|**Delete (Policy Version)**|Delete the selected policy version.|  
|**Delete (Rule)**|Delete the selected rule.|  
|**Delete**|Delete the selected policy and all its versions.|  
|**Add New Rule**|Create a new rule in the selected policy version.|  
|**Save**|Save any changes made to the selected version and its rules.|  
|**Publish**|Publish the selected policy version. Note that you cannot directly modify a published version. You can copy and paste it to a new version on the policy.|  
|**Reload**|Reload the selected policy version and its rules, with the option to discard any current changes made in that version and restore the contents from the rule store.|  
|**Deploy**|Deploy a published policy version. You must deploy a policy version to make it available to rule-based applications.|  
|**Undeploy**|Undeploy a policy version. After a version is undeployed, it is no longer available to rule-based applications.|  
|**Test Policy**|Test the selected policy version before deployment.|  
  
## Properties window  
 The following table describes the properties for a policy version.  
  
|Property|Value|  
|--------------|-----------|  
|**Name**|Name of the policy.<br /><br /> You can only change this value by changing the **Name** property of the policy (not policy version).|  
|**Fact Retriever**|Information about the fact retriever for the policy version.|  
|**Maximum Execution Loop Depth**|Maximum depth of the forward-chaining algorithm before an execution loop exception is thrown.<br /><br /> The default loop count is 65536.|  
|**Translation Duration**|Maximum amount of time to translate the rules before a translation time-out exception is thrown.<br /><br /> The default is 60000 milliseconds.|  
|**Translator**|Information about the translator used to translate the rules.|  
|**Current Version**|The version of policy currently selected in the Policy Explorer.|  
|**Version Description**|The description of the current version.|  
  
 The following table describes the properties for a rule.  
  
|Property|Value|  
|--------------|-----------|  
|**Active**|Indicates whether the rule is enabled or disabled|  
|**Name**|Name of the rule.|  
|**Priority**|Priority of the rule within the policy. The higher the index, the higher the rule priority. Actions of a higher priority rule will fire first.<br /><br /> The default is 0 and represents the middle priority.|
