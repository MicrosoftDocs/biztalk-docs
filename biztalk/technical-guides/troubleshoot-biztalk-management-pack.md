---
description: "Learn more about: Troubleshooting"
title: "Troubleshooting the BizTalk Server Management Pack | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 676fd891-ee7f-49fc-a6d7-204dc6f2f382
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting
There are a number of actions that you can take to troubleshoot BizTalk Server management pack issues:  
  
-   Ensure that Operations Manager is installed properly.  
  
-   Ensure that Operations Manager configuration settings are set properly.  
  
-   Verify that your import of the Management Pack is complete and successful.  
  
-   Ensure that all relevant entities are enabled, such as rules and monitors.  
  
-   Ensure that the computer groups are populated with the correct computers. You can use the **Authoring** mode **Groups** node in the console to perform this inspection.  
  
-   Ensure that all the SCOM agents are healthy.  
  
-   Ensure that the heartbeat interval is set properly and that the rules are propagated to the Operations Manager 2007 R2/2012 agent computer.  
  
-   Ensure that all performance counters are properly installed.  
  
## Known Issues
The following table lists all the known issues with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack for Operations Manager.  
  
|Issue|Description|Resolution|  
|-----------|-----------------|----------------|  
|Performance counter related errors and warnings after restart|You might see performance counter-related errors and warnings in the Operations Manager event log after agent restart.|The Management Pack recovers after the errors and resumes working.|  
|Objects discovery related warnings in the Operations Manager event Log|When a discovery (including relationship discovery) fails to find an instance, a warning is written to the Operations Manager event log stating that null was returned by the discovery script.||  
|Alerting in physical node in clustered environment is unreliable|There are two known issues associated with monitoring in clustered environments:<br /><br /> -   When a node changes from active to passive, the monitoring status of the node and associated artifacts may not be reflected correctly in the Operations Console.<br />-   In clustered environments, the Operations Manager creates a virtual node which may display duplicate status and alerts.|In clustered environments that contains active/passive nodes; rely on the monitoring information displayed in the virtual node only. This is because the virtual node always points to the physical node that is active at any point in time.|  
|Relationships and Dependency monitors|The following are the known issues related to relationships and dependency monitors: This occurs mostly when the BizTalk Management Pack is re-imported on a given SCOM Server. The user is then required to see comment the previous state as given in the "Steps to Reproduce the Behavior" section.<br /><br /> -   Relationships between BizTalk artifacts are not discovered.<br />-   Dependency relationships are not displayed as expected.<br />-   Roll up of monitoring status does not occur.<br />-   Some dependency monitors are uninitialized even after relationship discovery.|The workarounds to address these issues are as follows:<br /><br /> <ul><li>Restart the Operations Manager Health Service on the BizTalk agent machine. <br />     -OR-</li><li>Run the Flush Health Service State and Cache task. The steps to do this are as follows:<br /><br /> <ol><li>In the navigation tree, select Operations Manager Agent Agent Health State.</li><li>Select the computer that is running BizTalk Server under Agent State from Health Service Watcher.</li><li>Select the agent state under Agent State.</li><li>Click the Flush Health Service State and Cache task in the right-side panel.</li><li>In the Run Task - Flush Health Service State and Cache dialog box, click Run.</li></ol></li></ul>|  
|Displays wrong status of send ports and receive locations|When the SSO service is down, the BizTalk Server Management Pack does not show the correct status of send ports and receive locations.||
