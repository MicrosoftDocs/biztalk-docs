---
description: "Learn more about: Routine Monitoring Tasks"
title: "Routine Monitoring Tasks"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Routine Monitoring Tasks
Performing the following monitoring tasks on a regularly scheduled basis will assist you in keeping your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications and infrastructure operationally ready.

## Daily Monitoring Tasks

- Review all open alerts.

- Use the **Group Hub** page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console to investigate orchestration, port, and message failures. The **Group Hub** page provides access to the current real-time state of the system, accessing data in the MessageBox database. You can view all service instances such as orchestrations, ports, and messaging, along with their associated messages. Using the **Group Hub** page you can perform the following activities:

  - See currently running service instances, such as orchestrations and messaging, and their associated messages.

  - Look into the MessageBox database for a view of the current data and the real-time state of the system.

  - Suspend, terminate, and resume service instances.

    For more information about using the **Group Hub** page, see [Using the Group Hub Page](../core/using-the-group-hub-page.md).

- Review warnings (optional).

  For more information, see [Checklist: Performing Daily Maintenance Checks](checklist-performing-daily-maintenance-checks.md).

## Weekly Monitoring Tasks

- Review the event logs at least once per week. The reason for this task is to prevent issues, such as DBNetLib errors going undetected. Service interruption might go unnoticed unless you have a very low latency system. However, some of these errors can indicate a bigger issue (for example, too many hosts or BizTalk Server servers for the number of message boxes, performance issues on the SQL box, etc).

  For more information, see [Checklist: Performing Weekly Maintenance Checks](checklist-performing-weekly-maintenance-checks.md).

## As-Needed Tasks

- Modify the rules to customize the monitoring of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications and infrastructure.

- Run the Performance Analysis of Logs tool (PAL). If your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment is fairly constant (for example, new trading partners aren't added routinely, new code is not deployed), you might run Perfmon and PAL once a quarter or even every six months. If your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment changes more frequently, you may want to run Perfmon and PAL every couple of months to compare against a baseline. For more information on PAL, see [Using the Performance Analysis of Logs (PAL) Tool](using-the-performance-analysis-of-logs-pal-tool.md).

- Run Perfmon every few months, to once a quarter or even every six months depending on the number of changes occur in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.

- Run BizTalk Server Best Practices Analyzer when the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment changes (for example, the addition of new applications or creation of new hosts). You can [download the BizTalk Server Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=43382).

- Run the BizTalk MsgBoxViewer tool, which is available in the [BizTalk Health Monitor](../core/monitoring-biztalk-server.md). This tool analyzes the BizTalk MessageBox and other databases and generates an HTML report containing warnings, if any, and other information related to the databases.

  > [!TIP]
  >  You can also save the reports for later use. These reports might be useful when troubleshooting issues with the BizTalk application.

  > [!NOTE]
  >  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.

- Run the Terminator tool, which is available in the [BizTalk Health Monitor](../core/monitoring-biztalk-server.md). This tool enables users to easily resolve any issues identified by the BizTalk MsgBoxViewer tool.

  > [!NOTE]
  >  Use of this tool is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this programs. Use of this program is entirely at your own risk.

## Annual Monitoring Tasks

- Review the effectiveness of the monitoring of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications and infrastructure.

- Create a plan to make any needed changes in monitoring.

## See Also
 [Routine Maintenance Checklists](routine-maintenance-checklists.md)