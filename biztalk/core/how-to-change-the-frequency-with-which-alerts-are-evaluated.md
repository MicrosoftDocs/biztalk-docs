---
description: "Learn more about: How to Change the Frequency With Which Alerts Are Evaluated"
title: "How to Change the Frequency With Which Alerts Are Evaluated | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68f326ed-2017-4853-89b9-146cb0785554
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Change the Frequency With Which Alerts Are Evaluated
There are cases in which the SQL Notifications services generator may not keep up with events being raised by the BAM event provider when deployed with the default settings. You can increase the frequency (the quantum duration) with which events are evaluated for alerts by modifying the Notification Services adf.xml file.

## Prerequisites
 To perform this procedure you must be logged on as a member of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group that has permissions to read and write the Primary Import database, typically this will be a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.

### To modify the Notification Services generator quantum duration

1.  Open the Notification Services Command prompt. Click **Start**, click **All Programs**, click **Microsoft SQL Server 2005**, click **Configuration Tools**, and then click **Notification Services Command Prompt**.

2.  Get the Notification Services configuration file. At the command prompt, type: **cscript ProcessBamNSFiles.vbs -Get config.xml adf.xml \<PimaryImport database server\> \< PimaryImport database name\>**.

3.  Modify or add the \<QuantumDuration\> element under the \<ApplicationExecutionSettings\> node in the in the adf.xml file. For more information on the QuantumDuration element, see [https://go.microsoft.com/fwlink/?LinkId=78803](https://go.microsoft.com/fwlink/?LinkId=78803).

4.  At the command prompt, type: **cscript ProcessBamNSFiles.vbs -Update  config.xml adf.xml  \<PimaryImport database server\> \< PimaryImport database name\>.**

## See Also
 [BAM Command-Line Script for Notification Services Configuration Files](../core/bam-command-line-script-for-notification-services-configuration-files.md)
