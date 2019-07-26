---
title: WCF-Custom Transport Properties Dialog Box, Send, Behavior Tab
TOCTitle: WCF-Custom Transport Properties Dialog Box, Send, Behavior Tab
ms:assetid: 4e860c1a-d283-48d8-9a7f-c322dfaa374b
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246084(v=BTS.80)
ms:contentKeyID: 51527938
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.transport.send.behavior
---

# WCF-Custom Transport Properties Dialog Box, Send, Behavior Tab

 

You can use the **Behavior** tab to configure the endpoint behavior for this send port. An endpoint behavior is a set of the behavior extension elements that modify or extend service or client functionality. For example, the **callbackTimeOuts** behavior extension element specifies the interval of time within which transactions must complete or be automatically terminated. You can also import and export these settings through the **Import/Export** tab.


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
<td>Display the behavior extension elements configured for this send port. Use the <strong>Select Behavior Extension</strong> dialog box to add or remove the behavior extension elements. To open the dialog box, right-click <strong>EndpointBehavior</strong> in the <strong>Behavior</strong> tree view, and then click <strong>Add extension</strong>. <strong>Note:</strong> You cannot edit collection type properties such as <strong>ScopedCertificates</strong>. You must import a configuration file on the <strong>Import/Export</strong> tab to configure these properties. For more information about how to specify <strong>ScopedCertificates</strong> in a configuration file, see the WCF product documentation.<br />
<br />
The default value is <strong>EndpointBehavior</strong>.</td>
</tr>
<tr class="even">
<td><strong>Select Behavior Extension</strong></td>
<td>Select a behavior extension element to add to the endpoint behavior. To open this dialog box, right-click <strong>EndpointBehavior</strong> in the <strong>Behavior</strong> tree view, and then click <strong>Add extension</strong>. <strong>Note:</strong> Behavior extension elements already added to the endpoint behavior are not shown in the <strong>Select Behavior Extension</strong> dialog box.</td>
</tr>
<tr class="odd">
<td><strong>Reset all</strong></td>
<td>Restore the defaults for the <strong>Behavior</strong> tree view and the <strong>Configuration</strong> list view. To run this command, right-click <strong>EndpointBehavior</strong> in the <strong>Behavior</strong> tree view, and then click <strong>Reset all</strong>.</td>
</tr>
<tr class="even">
<td><strong>Remove extension</strong></td>
<td>Remove the behavior extension selected in the <strong>Behavior</strong> tree view. To run this command, right-click a behavior element in the <strong>Behavior</strong> tree view, and then click <strong>Remove extension</strong>.</td>
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

[The \<behaviors\> element](http://go.microsoft.com/fwlink/?linkid=75851)  
[How to Configure a WCF-Custom Send Port](https://msdn.microsoft.com/library/bb226446\(v=bts.80\))

