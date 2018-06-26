---
title: "Removing Usage Rule Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "policies, deleting rules"
  - "rules"
ms.assetid: b2b0dabf-8f99-4b85-95da-6bbf3e79ad41
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Removing Usage Rule Validation
Usage rules are defined in SWIFT standards and enforced by [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] business policies specific to each message type. These usage rules are guidelines that you can use to provide extra validation for a field. Unlike network validation rules, which are mandatory, you can choose not to require usage rules for a message type. If that is the case, you can do either of the following:  

-   You can remove a specific business rule that enforces a usage rule from the message-type validation policy.  

    > [!IMPORTANT]
    >  Removing a rule from the policy will remove it permanently.  

-   If you do not want to enforce any of the usage rules, you can undeploy the validation policy for a message type.  

### To remove a rule from a policy  

1.  In a text editor, such as Notepad, open the validation policy that you want to change, for example, MT103_Validation_Policy in *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103.  

2.  Remove the rule node that you do not want, and then save the policy.  

3.  Use the Business Rules Engine Deployment Wizard to publish and deploy the policy.  

    > [!NOTE]
    >  You can also remove a rule from a validation policy by creating a copy of the policy, removing the specific rule, and then deploying the modified policy. Undeploy the previous version of the policy.  

    > [!NOTE]
    >  In Business Rule Composer, you cannot delete a rule from a published or deployed policy.  

### To remove the policy for a message type  

1. Click **Start**, point to **Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.  

2. In Policy Explorer, find the deployed validation policy for the message type, for example, MT103_Validation_Policy.  

3. Right-click the policy, click **Undeploy**, click **Delete**, and then click **Yes**.
