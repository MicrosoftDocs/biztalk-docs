---
title: SOAP Transport Properties Dialog Box, Web service Tab
TOCTitle: SOAP Transport Properties Dialog Box, Web service Tab
ms:assetid: ea43d93b-5f97-479c-a9af-193f3218adb0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561719(v=BTS.80)
ms:contentKeyID: 51533140
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.soap.transport.webservice
---

# SOAP Transport Properties Dialog Box, Web service Tab

 

In the **SOAP Transport Properties** dialog box, use the **Web Service** tab to configure the send port for the SOAP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Orchestration Web Port</strong></td>
<td>Specify to use the Web service that is exposed at the Web Service URL listed on the General tab.<br />
<br />
This is the default setting.</td>
</tr>
<tr class="even">
<td><strong>Assembly name</strong></td>
<td>Specify the name of the assembly containing the Web service proxy. This field can be populated by clicking the browse button to find an assembly. After selecting the assembly this box is populated with the fully qualified name of the assembly.</td>
</tr>
<tr class="odd">
<td><strong>Type name</strong></td>
<td>Specify the name of the class that contains the Web method to be invoked. This can be selected from list of types contained within the assembly.</td>
</tr>
<tr class="even">
<td><strong>Method name</strong></td>
<td>Specify one of the methods in the list box or choose the option to &quot;Specify later.&quot; If the option to &quot;Specify later&quot; is chosen, the Web method must be set by some other means, such as a pipeline component. This pipeline component would be placed in the preassemble stage of the pipeline.</td>
</tr>
<tr class="odd">
<td><strong>SOAP 1.2</strong></td>
<td>Specify to generate proxy code that will support the SOAP 1.2 protocol. If this option is not selected, SOAP 1.1-compliant proxy code will be generated.<br />
<br />
Default value: Not selected.</td>
</tr>
</tbody>
</table>


## See Also

[Publishing Web Services](https://msdn.microsoft.com/en-us/library/aa561809\(v=bts.80\))

