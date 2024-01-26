---
description: "Learn more about: Domain Properties"
title: "Domain Properties2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_Domain"
---
# Domain Properties
The following tabs are available for the SNA Subdomain Properties sheet:  
  
## Domain Properties: NetView  
 NetView sends alerts back and forth between a host system and the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] and associated client computers.  
  
 **Send NetView Management Data to this Connection**  
 Select a connection to which NetView data should be sent. This can be any host connection.  
  
## Domain Properties: Display Verb  
 **Default Connection for Display**  
 Select a connection for use by Display Verbs. When the Display Verb is used but does not specify a connection, [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] uses the connection you specify in **Display Verb Properties**. If you do not specify a default Display connection, Host Integration Server randomly selects a connection for the verb to use.  
  
## Domain Properties: Server Broadcasts  
 Servers communicate with each other using server broadcasts.  
  
 **Mean Time between Server Broadcasts**  
 The interval at which server broadcasts are repeated. Broadcasts of state changes (such as the activation of a server) do not wait for this interval; instead, broadcasts are repeated at this interval to ensure reception (since broadcasts by definition are not guaranteed to be received).  
  
 Specifying a larger value causes less demand on the network (since broadcasts occur less often). However, a smaller value compensates better for loss of broadcast messages.  
  
 The range is from 45 through 65535 seconds; the default is **60** seconds.  
  
 **Network Transport for server Broadcasts**  
 Choose only the protocols you need, because sending unneeded broadcasts can significantly decrease network efficiency.  
  
## Domain Properties: Security  
 An administrator can adjust the subdomain security settings, including user permissions, configuration file ownership, and subdomain security events to audit.  
  
 **LU Types**  
 Select the **LU Types** (3270, LUA, or APPC) to which the security settings will apply. If security for an LU type is off, anyone who knows the LU name can use it. If security is on, only users to whom the LU is assigned can use it. The default setting is on for 3270, and off for LUA and APPC.  
  
 **Configuration File**  
 To view or change user permissions on the configuration file, click **Permissions**.  
  
 To view or change audited events, click **Auditing**.  
  
 To view or change configuration file ownership, click **Take Ownership**.  
  
## Domain Properties: Client Backup Configuration  
 **Disable Sending Client Backup Information**  
 The server sends no information to the client computer.  
  
 **Backup Domain**  
 The server updates the client computer with the backup SNA subdomain name specified in the box.  
  
 **Backup Sponsor Servers**  
 The server updates the client computer with all of the SNA Sponsor Server names (shown in the box). The maximum is 15.  
  
## Domain Properties: Error / Audit Logging  
 You can use information from the Windows event logs as you test a configuration or to diagnose a problem.  
  
 **Centralized Event Log Server**  
 Select the name of the server on which Windows event logs for this server installation should be stored.  
  
 **Route All Popup Messages to**  
 Select the name of the server to which pop-up error messages should be routed.  
  
 **Default Audit Log Level**  
 Select a level  
  
 **Detailed problem analysis:** To record all events that can be recorded, select this option.  
  
 **General information messages:** To record general activity but not all events, select this option.  
  
 **Significant system events:** To record only major events, select this option.  
  
 **Audit logging disabled:** To turn off audit logging, select this option.  
  
## Domain Properties: Response Time Monitor (RTM)  
 Response Time Monitor tracks the time it takes a host to respond to 3270 session requests. RTM is supported only by certain emulators. You should configure RTM only if the emulators you are using support RTM.  
  
 **RTM Data Sent at**  
 Select one or both of the following:  
  
 **Counter Overflow:**  
  
 To cause RTM data to be sent to the host when the number of host responses in a given time period overflows the size of the available counter, select this box.  
  
 **End of Session:**  
  
 To cause RTM data to be sent to the host at the end of each LU-to-LU session, select this box.  
  
 **RTM Timers Run Until**  
 Select the point at which RTM will register that a host has responded; this is when RTM stops the timers. (The timers are started when the local system sends data.)  
  
 **First Data Reaches Screen:**  
  
 To stop timing when data reaches the local screen, select this option.  
  
 **Host Unlocks Keyboard:**  
  
 To stop timing when the host unlocks the local keyboard, select this option.  
  
 **Host Lets User Send:**  
  
 To stop timing when the host lets the local computer send more data, select this option.  
  
 **RTM Thresholds**  
 Specify the cutoff times, in tenths of a second, at which RTM saves its count of host responses, and then restarts the count. For example, you could specify 5, 10, 20, and 50, to save the count of host responses during the intervals from 0.0 to 0.5 seconds, from 0.5 to 1.0 seconds, from 1.0 to 2.0 seconds, and from 2.0 to 5.0 seconds.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help1.md)
