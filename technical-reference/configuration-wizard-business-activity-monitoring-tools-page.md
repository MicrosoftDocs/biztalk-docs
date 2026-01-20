---
description: "Learn more about: Configuration Wizard, Business Activity Monitoring - Tools Page"
title: Configuration Wizard, Business Activity Monitoring - Tools Page
TOCTitle: Configuration Wizard, Business Activity Monitoring - Tools Page
ms:assetid: 6e84dfe8-6ea6-42a0-9f71-02da594aead3
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560722(v=BTS.80)
ms:contentKeyID: 51528805
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.config.wizard.bam.runtime
ms.topic: ui-reference
---

# Configuration Wizard, Business Activity Monitoring - Tools Page

 

Use the **Business Activity Monitoring - Tools** page to configure the server with monitoring tools for business users.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Enable Business Activity Monitoring tools</strong></td>
<td>Select <strong>Enable Business Activity Monitoring tools</strong> to enable the tools.</td>
</tr>
<tr class="even">
<td><strong>Enable Analysis Services for BAM aggregations</strong></td>
<td>Select <strong>Enable Analysis Services for BAM aggregations</strong> to provide tracking information for BAM alerts.</td>
</tr>
<tr class="odd">
<td><strong>Data stores</strong></td>
<td>The Data stores list provides an editable view of the server name and databases used for BAM tools.</td>
</tr>
</tbody>
</table>


Use the **Business Activity Monitoring - Alerts** page to configure subscription-based notification services.


> [!NOTE]
> <P>BAM alerts require BAM tools to be enabled.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Enable SQL Notification Services for BAM alerts</strong></td>
<td>Select <strong>Enable SQL Notification Services for BAM alerts</strong> to enable BAM alerts.</td>
</tr>
<tr class="even">
<td><strong>Windows service</strong></td>
<td>The Windows service list provides an editable view of the account used to run the BAM Notification Service.</td>
</tr>
<tr class="odd">
<td><strong>BAM Alerts SMTP Server</strong></td>
<td>Type the name of the SMTP server that will be used to send the BAM alerts.</td>
</tr>
<tr class="even">
<td><strong>BAM Alerts File Location</strong></td>
<td>Type the name of the network share that will be used to store the BAM alerts. <strong>Note:</strong> You will need to manually create this share before BAM alerts will store the files.</td>
</tr>
<tr class="odd">
<td><strong>SQL Server for Alerts Databases</strong></td>
<td>Type the name of the SQL server that will be used for the Alerts database.</td>
</tr>
<tr class="even">
<td><strong>Prefix for Alerts Database Names</strong></td>
<td>Type a prefix that will be used for the Alerts databases.</td>
</tr>
</tbody>
</table>


## See Also

[Installation Overview for BizTalk Server 2013 and 2013 R2](https://msdn.microsoft.com/library/jj248688\(v=bts.80\))[Getting Started](https://msdn.microsoft.com/library/aa560946\(v=bts.80\))

