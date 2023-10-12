---
description: "Learn more about: How to Configure Tracking for a Policy"
title: "How to Configure Tracking for a Policy"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure Tracking for a Policy
This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administration console to configure tracking for a policy. You can select options to view instance data, results of conditions, actions, and agenda updates in the query views of the administration console Group Hub page.  
  
 For more information about creating and using queries, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md). For more information about the message and service instance  tracking features of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To configure tracking for a policy  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure tracking for a policy.  
  
3. Click **Policies**, right-click the policy, click **Properties**, and then click **Tracking**.  
  
4. Select the tracking options you want, as described in the following table, and then click **OK**.  
  
   |Use this|To do this|  
   |--------------|----------------|  
   |**Fast activity**|Select this check box to track the instance data on which the policy operates.|  
   |**Condition evaluation**|Select this check box to track the true/false results of conditions in the selected policy.|  
   |**Rule firings**|Select this check box to track the actions started as a result of the policy.|  
   |**Agenda updates**|Select this check box to track updates to the agenda. The agenda contains a list of actions that are "true" and need to fire.|  
  
## See Also  
 [Managing Policies](../core/managing-policies.md)
