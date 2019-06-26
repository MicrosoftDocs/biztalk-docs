---
title: Policies Node, Details Pane
TOCTitle: Policies Node, Details Pane
ms:assetid: fe4dfc1d-299e-4af1-a7fc-29045f3b9b6c
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562147(v=BTS.80)
ms:contentKeyID: 51533786
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.resultsobject.policy
---

# Policies Node, Details Pane

 

Use the Policies node details pane to manage policies in the application.

Right-click a specific policy to display the following commands:

  - **Deploy**. Changes the state of the policy from published to deployed.

  - **Undeploy**. Changes the state of the policy from deployed to published.

  - **Publish**. Makes a policy available to be added to applications. This command is available only for policy objects contained in **\<All Artifacts\>**. The **Publish** command appears when a rule that was created in the Rule Composer was saved but not published.

  - **Remove**. If the policy is published, **Remove** deletes the policy from the Rules database. If the policy is deployed, **Remove** disassociates the policy from the current application, but does not delete it from the Rules database; the policy is still visible under the **All Artifacts** console tree node.

  - **Move To Application**. Displays the **Move to Application** dialog box, which you use to move artifacts from the current application in the Administrative Console to a different application.

  - **Export**. Displays the **Export Policies** dialog box, where you can selectively export business rules and vocabularies to an \*.xml file.

  - **Properties**. Displays the **Policy Properties** dialog box.

## See Also

[Importing BizTalk Applications, Bindings, and Policies](https://msdn.microsoft.com/library/aa560565\(v=bts.80\))

