---
title: WCF-Custom Transport Properties Dialog Box, Receive, Behavior Tab
TOCTitle: WCF-Custom Transport Properties Dialog Box, Receive, Behavior Tab
ms:assetid: 518172d2-4213-493b-8f7c-f1ef78c25732
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb246096(v=BTS.80)
ms:contentKeyID: 51528012
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.transport.receive.behavior
---

# WCF-Custom Transport Properties Dialog Box, Receive, Behavior Tab

 

Use the **Behavior** tab to configure the endpoint and service behaviors for this receive location. An endpoint behavior is a set of behavior extension elements that modify or extend service or client functionality. For example, the **callbackTimeOuts** behavior extension element specifies the interval of time for the client callback within which transactions must complete or be automatically terminated. A service behavior is a set of behavior extension elements that modify or extend service functionality. For example, the **serviceTimeOuts** behavior extension element specifies the interval of time for a service within which transactions must complete or be automatically aborted. You can also import and export these settings through the **Import/Export** tab.


> [!NOTE]
> <P>Service behaviors affect only service-related aspects, and endpoint behaviors affect only endpoint-related properties.</P>




> [!NOTE]
> <P>BizTalk Server does not support all the types of the behavior extension elements that you can configure on the <STRONG>Behavior</STRONG> tab.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Behavior</strong></td>
<td>Display the service and endpoint behavior and their behavior extension elements configured for this receive location. Use the <strong>Select Behavior Extension</strong> dialog box to add or remove the behavior extension elements for each behavior. To open the dialog box, right-click <strong>EndpointBehavior</strong> or <strong>ServiceBehavior</strong> in the <strong>Behavior</strong> tree view, and then click <strong>Add extension</strong>. <strong>Note:</strong> You cannot edit collection type properties such as <strong>ScopedCertificates</strong>, <strong>AuthorizationPolicies</strong>, and <strong>KnownCertificates</strong>. You must import a configuration file on the <strong>Import/Export</strong> tab to configure these properties. For more information about how to specify <strong>ScopedCertificates</strong>, <strong>AuthorizationPolicies</strong>, and <strong>KownCertificates</strong> in a configuration file, see the WCF product documentation.<br />
<br />
The default values are <strong>EndpointBehavior</strong> and <strong>ServiceBehavior</strong>. <strong>Note:</strong> In order for the impersonation scenario to work in the WCF-Custom receive adapter, you must add the <strong>serviceAuthorization</strong> extension under the <strong>ServiceBehavior</strong> and then set the <strong>ImpersonateCallerForAllOperations</strong> to <strong>true</strong> as well as select the <strong>Issue Single Sign-On ticket</strong> option under the <strong>Other</strong> tab in the <strong>WCF-Custom Transport Properties</strong> dialog.</td>
</tr>
<tr class="even">
<td><strong>Select Behavior Extension</strong></td>
<td>Select a behavior extension element to add to the behavior selected in the <strong>Behavior</strong> tree view. To open this dialog box, right-click <strong>ServiceBehavior</strong> or <strong>EndpointBehavior</strong> in the <strong>Behavior</strong> tree view, and then click <strong>Add extension</strong>. <strong>Note:</strong> Behavior extension elements already added to the behavior are not shown in the <strong>Select Behavior Extension</strong> dialog box.</td>
</tr>
<tr class="odd">
<td><strong>Reset all</strong></td>
<td>Restore the defaults for the behavior selected in the <strong>Behavior</strong> tree view, and the behavior's extension elements in the <strong>Configuration</strong> list view. To run this command, right-click <strong>ServiceBehavior</strong> or <strong>EndpointBehavior</strong> in the <strong>Behavior</strong> tree view, and then click <strong>Reset all</strong>.</td>
</tr>
<tr class="even">
<td><strong>Remove extension</strong></td>
<td>Remove the behavior extension element selected in the <strong>Behavior</strong> tree view. To run this command, right-click a behavior element in the <strong>Behavior</strong> tree view, and then click <strong>Remove extension</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Move extension up</strong></td>
<td>Move up the order of the behavior extension element selected in the <strong>Behavior</strong> tree view. To run this command, right-click a behavior element in the <strong>Behavior</strong> tree view, and then click <strong>Move extension up</strong>.</td>
</tr>
<tr class="even">
<td><strong>Move extension down</strong></td>
<td>Move down the order of the behavior extension element selected in the <strong>Behavior</strong> tree view. To run this command, right-click a behavior element in the <strong>Behavior</strong> tree view, and then click <strong>Move extension down</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Configuration</strong></td>
<td>Display the attributes and their values for the behavior element selected in the <strong>Behavior</strong> tree view. You can also modify the attribute values using this list view.</td>
</tr>
<tr class="even">
<td><strong>Restore Defaults</strong></td>
<td>Restore the defaults for the <strong>Behavior</strong> tree view and the <strong>Configuration</strong> list view.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-Custom Receive Location](https://msdn.microsoft.com/en-us/library/bb259941\(v=bts.80\))  
[How to Configure a WCF-CustomIsolated Receive Location](https://msdn.microsoft.com/en-us/library/bb226374\(v=bts.80\))  
[The \<behaviors\> element](http://go.microsoft.com/fwlink/?linkid=75851)

