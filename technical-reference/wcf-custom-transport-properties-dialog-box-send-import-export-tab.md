---
title: WCF-Custom Transport Properties Dialog Box, Send, Import-Export Tab
TOCTitle: WCF-Custom Transport Properties Dialog Box, Send, Import-Export Tab
ms:assetid: 21be00d0-ca23-4531-bd59-0bfbda135a7d
ms:mtpsurl: https://msdn.microsoft.com/library/Bb245995(v=BTS.80)
ms:contentKeyID: 51526779
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.transport.send.importexport
---

# WCF-Custom Transport Properties Dialog Box, Send, Import-Export Tab

 

Use the **Import/Export** tab to import and export the **Address (URI)** and **Endpoint Identity** properties, binding information on the **Binding** tab, and endpoint behavior on the **Behavior** tab for this send port.


> [!NOTE]
> <P>You need to click Apply to apply the changes you make in the transport properties dialog box before you can export the WCF configuration to a .config file.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Import</strong></td>
<td>Display the <strong>Import WCF configuration</strong> dialog box, which you use to import the <strong>Address (URI)</strong> and <strong>Endpoint Identity</strong> properties, binding information on the <strong>Binding</strong> tab, and endpoint behavior on the <strong>Behavior</strong> tab for this send port from a configuration file.</td>
</tr>
<tr class="even">
<td><strong>Export</strong></td>
<td>Display the <strong>Export WCF configuration</strong> dialog box, which you use to export the <strong>Address (URI)</strong> and <strong>Endpoint Identity</strong> properties, binding information on the <strong>Binding</strong> tab, and endpoint behavior on the <strong>Behavior</strong> tab to a configuration file. <strong>Note:</strong> If the send port is configured to use multiple identity types for <strong>Endpoint Identity</strong>, only the identity type with the lowest number can be exported. For example, if <strong>1. DNS</strong> and <strong>4. RSA</strong> are both set in the <strong>Identity Editor</strong> dialog box, only the <strong>1. DNS</strong> property is saved by using the <strong>Export</strong> tab.</td>
</tr>
<tr class="odd">
<td><strong>Import WCF configuration</strong></td>
<td>Select a configuration file from which to import the <strong>Address (URI)</strong> and <strong>Endpoint Identity</strong> properties, binding information on the <strong>Binding</strong> tab, and endpoint behavior on the <strong>Behavior</strong> tab. After selecting a configuration, you can specify the endpoint configuration to import from the <strong>Select Endpoint</strong> dialog box. <strong>Note:</strong> The WCF configuration files may contain the <strong>&lt;headers&gt;</strong> element to specify a collection of custom address headers, but the WCF-Custom adapter does not import and use the <strong>&lt;headers&gt;</strong> element. To use SOAP headers with the WCF send adapters, you use the <strong>WCF.OutboundCustomHeaders</strong> property. For more information about how to consume WCF Services with custom SOAP headers, see the related topic listed in See Also section of this topic.</td>
</tr>
<tr class="even">
<td><strong>Export WCF configuration</strong></td>
<td>Select a configuration file to which to export the <strong>Address (URI)</strong> and <strong>Endpoint Identity</strong> properties, binding information on the <strong>Binding</strong> tab, and endpoint behavior on the <strong>Behavior</strong> tab.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-Custom Send Port](https://msdn.microsoft.com/library/bb226446\(v=bts.80\))  
[SOAP Headers with Consumed WCF Services](https://msdn.microsoft.com/library/bb245946\(v=bts.80\))

