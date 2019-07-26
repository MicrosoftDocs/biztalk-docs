---
title: BizTalk Settings Dashboard, Host Page, General Tab
TOCTitle: BizTalk Settings Dashboard, Host Page, General Tab
ms:assetid: 84de6f06-1074-4dc6-9873-5b4ec4a7f11c
ms:mtpsurl: https://msdn.microsoft.com/library/Ff629740(v=BTS.80)
ms:contentKeyID: 51529391
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# BizTalk Settings Dashboard, Host Page, General Tab

 

Use the **General** tab to modify the general configuration settings of a given host, across a BizTalk group.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
<th>Boundary values</th>
<th>Default value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Host</strong></td>
<td>From the drop-down list, select the host representing the BizTalk Server runtime instances.</td>
<td>-</td>
<td>-</td>
</tr>
<tr class="even">
<td><strong>Move tracking data to DTA DB</strong></td>
<td>Indicate if the host loads the BizTalk Tracking component to process health monitoring and business data.<br />
<br />
If you select this check box, the current host will have read/write access to the tracking tables in the MessageBox database, as well as to the Tracking database. Accordingly, any objects running in this host will also have read/write access to these databases.<br />
<br />
If you do not select the check box, the host will have only write access to the tracking tables in the MessageBox database and will not have access to the Tracking database.</td>
<td>On, Off</td>
<td>On</td>
</tr>
<tr class="odd">
<td><strong>Trusted authentication</strong></td>
<td>Indicate whether a BizTalk host can be trusted to collect authentication information.<br />
<br />
By specifying which hosts are trusted and which are not, you can define the security boundaries in which user objects and code can be trusted or not trusted.</td>
<td>On, Off</td>
<td>Off</td>
</tr>
<tr class="even">
<td><strong>32-Bit only</strong></td>
<td>Indicate whether the host instance process should be created as 32-Bit on both 32-Bit and 64-Bit servers.</td>
<td>On, Off</td>
<td>On</td>
</tr>
<tr class="odd">
<td><strong>Default app-domain for isolated adapter</strong></td>
<td>Indicate whether the isolated adapter runs in the default app domain, or the domain of the caller.<br />
<br />
By default all messaging engine objects are created in the domain of the caller. If the Web service is inactive for an extended period of time for any reason, IIS unloads the caller domain. When this happens, all services in the hosting process become unusable.<br />
<br />
When you select the default AppDomain, the BizTalk Messaging Engine objects are created in the default AppDomain instead of in their own AppDomains. And, the default AppDomain is never unloaded.</td>
<td>On, Off</td>
<td>Off</td>
</tr>
<tr class="even">
<td><strong>Legacy whitespace behavior</strong></td>
<td>Specify if you do <strong>not</strong> want to preserve the white spaces during mapping.</td>
<td>On, Off</td>
<td>Off</td>
</tr>
<tr class="odd">
<td><strong>Allow multiple responses</strong></td>
<td>Indicate whether you want to enable multiple responses to be sent back to a 2-way receive location.</td>
<td>On, Off</td>
<td>Off</td>
</tr>
<tr class="even">
<td><strong>Response timeout</strong></td>
<td>Specify the default timeout for request response messages.</td>
<td>1 – Max value of type Integer</td>
<td>20</td>
</tr>
<tr class="odd">
<td><strong>Maximum engine threads</strong></td>
<td>Indicate the maximum number of messaging engine threads per CPU.<br />
<br />
This option specifies the maximum number of threads that can be used by the End Point Manager (EPM). The EPM starts with the number of threads equivalent to 10% of this value and adds threads up to the specified value as load increases. The number of threads allocated is reduced as load is reduced or as necessary for throttling.<br />
<br />
 <strong>Note:</strong> If you modify this value, the host needs to be restarted for the change to take effect.</td>
<td>[1,50]</td>
<td>20</td>
</tr>
<tr class="even">
<td><strong>Show performance counters for</strong></td>
<td>Select the service for which you want to display the performance counters.<br />
<br />
When set to Messaging, Performance Monitor will display Message Agent counters for messaging. If the host contains orchestrations, no Message Agent output for the orchestration (XLANG) instances will display.<br />
<br />
If the host only contains orchestrations, change the <strong>Show performance counters for</strong> setting to Orchestrations to display Message Agent counters for Orchestration instances. If the host only contains receive ports/send ports, keep the Messaging option to display Message Agent counters for Messaging instances.</td>
<td>Messaging, Orchestrations</td>
<td>Messaging</td>
</tr>
</tbody>
</table>


**Polling Intervals**

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
<th>Boundary values</th>
<th>Default value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Messaging</strong></td>
<td>Set the BizTalk Server polling interval in milliseconds when BizTalk host instance is looking for new messages in the MessageBox.</td>
<td>1 – Max value of type Integer</td>
<td>500</td>
</tr>
<tr class="even">
<td><strong>Orchestrations</strong></td>
<td>Set the BizTalk Server polling interval in milliseconds when BizTalk host instance is looking for new orchestrations in the database.</td>
<td>1 – Max value of type Integer</td>
<td>500</td>
</tr>
<tr class="odd">
<td><strong>Restore Defaults</strong></td>
<td>Click to cancel the modifications done and apply the default BizTalk settings.</td>
<td>-</td>
<td>-</td>
</tr>
</tbody>
</table>


## See Also

[How to Modify Group Settings](https://msdn.microsoft.com/library/ff629808\(v=bts.80\))  
[How to Modify Host Instance Settings](https://msdn.microsoft.com/library/ff629695\(v=bts.80\))

