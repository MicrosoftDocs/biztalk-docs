---
title: WCF-Custom Transport Properties Dialog Box, Receive, Binding Tab
TOCTitle: WCF-Custom Transport Properties Dialog Box, Receive, Binding Tab
ms:assetid: 68c748ba-3bc5-4582-8284-1cb941ef0940
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226331(v=BTS.80)
ms:contentKeyID: 51528659
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.transport.receive.binding
---

# WCF-Custom Transport Properties Dialog Box, Receive, Binding Tab

 

Use the **Binding** tab to configure different types of predefined or custom bindings for Windows Communication Foundation (WCF). You can also import and export these settings through the **Import/Export** tab.


> [!NOTE]
> <P>BizTalk Server does not support all the types of the binding extension elements that you can configure on the <STRONG>Binding</STRONG> tab.</P>



## Predefined Binding

Predefined bindings hide the complexity of the WCF messaging stack. Applications using predefined bindings do not require full control over the stack. The attributes exposed on each predefined binding are the ones most appropriate for the usage scenario the binding addresses. It is not possible to add elements or attributes to a predefined binding. To do so, you should implement a custom binding.


> [!NOTE]
> <P>The WCF-CustomIsolated adapter supports only the predefined bindings that Microsoft Internet Information Services (IIS) can host: <STRONG>wsHttpBinding</STRONG>, <STRONG>basicHttpBinding</STRONG>, <STRONG>wsFederationHttpBinding</STRONG>, and <STRONG>wsDualHttpBinding</STRONG>.</P>




> [!NOTE]
> <P>The WCF-CustomIsolated adapter does not support the predefined bindings for the metadata exchange protocol such as <STRONG>mexHttpBinding</STRONG> and <STRONG>mexHttpsBinding</STRONG>.</P>



## Custom Binding

Custom bindings provide full control over the WCF messaging stack. An individual binding defines the message stack by specifying the binding extension elements for the stack elements in the order they appear on the stack. Each binding extension element defines and configures one element of the stack. There must be one and only one `transport` binding extension element in each custom binding. Without this element, the messaging stack is incomplete.


> [!NOTE]
> <P>The WCF-CustomIsolated adapter supports only the transport binding extension elements that the IIS can host: <STRONG>httpTransport</STRONG> and <STRONG>httpsTransport</STRONG>.</P>



The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message. The recommended order of stack elements is the following:

1.  Transactions (optional)

2.  Reliable Messaging (optional)

3.  Security (optional)

4.  Transport

5.  Encoder (optional)

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Binding Type</strong></td>
<td>Specify the binding for this receive location. Bindings are objects used to specify the communication details required to connect to the endpoint of a WCF service. Each endpoint in a WCF service requires a binding to be well-specified. Valid values include the following:<br />
<br />
- <strong>basicHttpBinding</strong><br />
- <strong>basicHttpContextBinding</strong><br />
- <strong>customBinding</strong><br />
- <strong>mexHttpBinding</strong><br />
- <strong>mexHttpsBinding</strong><br />
- <strong>mexNamedPipeBinding</strong><br />
- <strong>mexTcpBinding</strong><br />
- <strong>netMsmqBinding</strong><br />
- <strong>netNamedPipeBinding</strong><br />
- <strong>netPeerTcpBinding</strong><br />
- <strong>netTcpBinding</strong><br />
- <strong>netTcpContextBinding</strong><br />
- <strong>webHttpBinding</strong><br />
- <strong>ws2007FederationHttpBinding</strong><br />
- <strong>ws2007HttpBinding</strong><br />
- <strong>wsDualHttpBinding</strong><br />
- <strong>wsFederationHttpBinding</strong><br />
- <strong>wsHttpBinding</strong><br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Binding</strong></td>
<td>Display the predefined binding elements if you select a predefined binding in the <strong>Binding Type</strong> property. When the <strong>Binding Type</strong> property is set to <strong>customBinding</strong>, you can edit binding extension elements through the <strong>Select Binding Element Extension</strong> dialog box. For more information about the available binding extension elements and the order in which they appear, see the preceding section, &quot;Custom Bindings.&quot; <strong>Note:</strong> You cannot edit collection type properties such as <strong>ClaimTypeRequirements</strong>. You must import a configuration file on the <strong>Import/Export</strong> tab to configure these properties. For more information about how to specify <strong>ClaimTypeRequirements</strong> in a configuration file, see the WCF product documentation.<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>Select Binding Element Extension</strong></td>
<td>Select a binding extension element to add to the custom binding. To open the <strong>Select Binding Element Extension</strong> dialog box, right-click <strong>CustomBindingElement</strong> in the <strong>Binding</strong> tree view, and then click <strong>Add extension</strong>. <strong>Note:</strong> Binding extension elements already added to the custom binding are not shown in the <strong>Select Binding Element Extension</strong> dialog box.</td>
</tr>
<tr class="even">
<td><strong>Reset all</strong></td>
<td>Restore the defaults for the <strong>Binding</strong> tree view and the <strong>Configuration</strong> list view when the <strong>Binding Type</strong> property is set to <strong>customBinding</strong>. To run this command, right-click <strong>CustomBindingElement</strong> in the <strong>Binding</strong> tree view, and then click <strong>Reset all</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Remove extension</strong></td>
<td>Remove the binding extension selected in the <strong>Binding</strong> tree view when the <strong>Binding Type</strong> property is set to <strong>customBinding</strong>. To run this command, right-click a binding element in the <strong>Binding</strong> tree view, and then click <strong>Remove extension</strong>.</td>
</tr>
<tr class="even">
<td><strong>Move extension up</strong></td>
<td>Move up the order of the binding extension element selected in the <strong>Binding</strong> tree view when the <strong>Binding Type</strong> property is set to <strong>customBinding</strong>. To run this command, right-click a binding element in the <strong>Binding</strong> tree view, and then click <strong>Move extension up</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Move extension down</strong></td>
<td>Move down the order of the binding extension element selected in the <strong>Binding</strong> tree view when the <strong>Binding Type</strong> property is set to <strong>customBinding</strong>. To run this command, right-click a binding element in the <strong>Binding</strong> tree view, and then click <strong>Move extension down</strong>.</td>
</tr>
<tr class="even">
<td><strong>Configuration</strong></td>
<td>Display the attributes and their values for the binding element selected in the <strong>Binding</strong> tree view. You can also modify the attribute values using this list view.</td>
</tr>
<tr class="odd">
<td><strong>Restore Defaults</strong></td>
<td>Restore the defaults for the <strong>Binding</strong> tree view and the <strong>Configuration</strong> list view.</td>
</tr>
</tbody>
</table>


## See Also

[The \<binding\> element](https://go.microsoft.com/fwlink/?linkid=75753)
[How to Configure a WCF-Custom Receive Location](https://msdn.microsoft.com/library/bb259941\(v=bts.80\))
[How to Configure a WCF-CustomIsolated Receive Location](https://msdn.microsoft.com/library/bb226374\(v=bts.80\))

