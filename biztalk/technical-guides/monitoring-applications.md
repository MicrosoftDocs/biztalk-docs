---
title: "Monitoring Applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4be98ba2-6acd-4dee-b6ea-db71bbd368f0
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring Applications
Setting up Microsoft System Center Operations Manager to monitor BizTalk applications typically can be broken down into a progressive four-step process as follows:  
  
1. **Modify existing rules and/or copy rules to a custom management pack to monitor a custom BizTalk application**  
  
    You will need to copy many of these rules multiple times. This is the case if you are monitoring a number of file shares, for example. In this scenario, you would copy the base rule once for each file share with the file share address added in the description field on the **Criteria** tab of the rule. By adding the address, Operations Manager will raise an alert for each individual file share. When you copy an existing rule, ensure that you select **Enable** rule-disable overrides for this rule or you will receive duplicate alerts.  
  
    Another item that you should add to each rule that you create is Knowledge information on the **Knowledge Base** tab of the rule property. This data is attached to the notification that is raised when Operations Manager sends out an alert. The power of this feature becomes clear when you include steps that may help resolve the error.  
  
2. **Create actions for each defined rule**  
  
    Creating or copying a rule is really the first step in the process. The next step is to take some action based on that rule. If there is no action based on a rule then it doesn’t really matter that the event was ever monitored. The action most frequently taken is to alert an operator or administrator that an error has occurred. Operations Manager also provides a number of other actions that can be used when an event is triggered. These actions include:  
  
   -   Starting a script  
  
   -   Sending a Simple Network Management Protocol (SNMP) trap (in SNMP, agents monitor the activity in the various devices on the network and report to the network console workstation)  
  
   -   Sending a notification to a Notification group  
  
   -   Executing a command or batch file  
  
   -   Updating a state variable  
  
   -   Transferring a file  
  
   -   Calling a method on a managed code assembly  
  
3. **Create iterative processes to automate manual tasks**  
  
    The next step is an iterative process and moves beyond the basic alerting mechanism. With Operations Manager able to invoke both script and .NET code, the process of automating manual tasks based on raised events is a powerful and time saving feature. An example of this is to run a script to automatically start a port if a disabled /stopped event message is logged. This process is iterative since many processes can be automated.  
  
4. **Use threshold rules to automate manual tasks**  
  
    The next step in processing is to move beyond the reactive alerting and use threshold rules. The BizTalk Server Management Pack does not contain any threshold rules by default. This is because such rules are typically specific to the custom application and are different for every application. A threshold embodies a business rule regarding the custom application and provides a proactive means of monitoring a system. You can use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] threshold templates provided with the Performance Analysis of Logs (PAL) tool to define rules.  
  
    An example of such a threshold rule is to measure when the CPUs on a server consistently run above 75 percent for a specific time period. This could indicate that you need to scale out the system. Yet another example is where you create a threshold rule that monitors a unique set of counters. This rule could then invoke code to initialize BizTalk host instances on a previously configured backup server during periods of high demand.  
  
## See Also  
 [Monitoring BizTalk Server with System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)