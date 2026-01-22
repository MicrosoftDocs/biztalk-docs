---
description: "Learn more about: SOAP Transport Properties Dialog Box"
title: SOAP Transport Properties Dialog Box
TOCTitle: SOAP Transport Properties Dialog Box
ms:assetid: 818c592d-eedf-4665-b40b-aba1cec5a9f5
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561089(v=BTS.80)
ms:contentKeyID: 51529296
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.soap.transport
---

# SOAP Transport Properties Dialog Box

 

Use the **SOAP Transport Properties** dialog box to configure the receive location for the SOAP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Virtual directory plus Web Service .asmx file</strong></td>
<td>Indicate the .asmx file created by the BizTalk Web Services Publishing Wizard.<br />
<br />
The format of this message follows this example:<br />
<br />
/PurchaseOrder/POOrchestration.asmx<br />
<br />
where the full location of the .asmx file is http://localhost/PurchaseOrder/POOrchestration.asmx.</td>
</tr>
<tr class="even">
<td><strong>Public address</strong></td>
<td>Specify the fully qualified URI for this receive location. The value for this property is a combination of the server name and the virtual directory.</td>
</tr>
<tr class="odd">
<td><strong>Use Single Sign-On</strong></td>
<td>Indicate that the SOAP adapter uses Enterprise Single Sign-On. <strong>Note:</strong> The BizTalk Web Services Publishing Wizard allows you to use Microsoft SharePoint Portal Server Single Sign-On; this property only enables Enterprise Single Sign-On.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a SOAP Receive Location](https://msdn.microsoft.com/library/aa561021\(v=bts.80\))

