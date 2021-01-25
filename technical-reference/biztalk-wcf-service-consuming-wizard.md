---
description: "Learn more about: BizTalk WCF Service Consuming Wizard"
title: BizTalk WCF Service Consuming Wizard
TOCTitle: BizTalk WCF Service Consuming Wizard
ms:assetid: 6f4fc7b6-5a85-4c90-ae89-2933c90f7325
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226343(v=BTS.80)
ms:contentKeyID: 51528828
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.wcf-service.consuming.wizard
---

# BizTalk WCF Service Consuming Wizard

 

Use the BizTalk WCF Service Consuming Wizard to generate the BizTalk artifacts, such as BizTalk orchestrations and types, to consume a WCF service based on the metadata document of the WCF service. For general usage information about the BizTalk WCF Services Consuming Wizard, see [Using WCF Services](https://msdn.microsoft.com/library/bb246032\(v=bts.80\)).

## Metadata Source Page

Use this page to select the source of the metadata to import.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Metadata Exchange (MEX) endpoint</strong></td>
<td>Consume metadata from the metadata exchange endpoint of a running service.<br />
<br />
The default value is selected.</td>
</tr>
<tr class="even">
<td><strong>Metadata Files (WSDL and XSD)</strong></td>
<td>Consume metadata from a set of Web Service Description Language (*.wsdl) and XML schema (*.xsd) files.<br />
<br />
The default value is cleared.</td>
</tr>
</tbody>
</table>


## Metadata Endpoint Page

Use this page to specify the Metadata Exchange (MEX) endpoint of the WCF service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Metadata Address (URL)</strong></td>
<td>Specify the URL to the running Web service that provides metadata for download through WS-Metadata Exchange or Http-Get. To get the metadata document from the URL, click <strong>Get</strong>.<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Edit</strong></td>
<td>Edit the user credential to use when downloading metadata documents from the service specified in the <strong>Metadata Address (URL)</strong> drop-down list. If the service requires user credentials with the basic authentication scheme, you must supply an appropriate user name and password to the service. This open the <strong>BizTalk WCF Service Consuming Wizard</strong> dialog box in which you can specify user name and password. <strong>Note:</strong> BizTalk WCF Service Consuming Wizard does not allow you to set certificate credentials in the wizard. To workaround this limitation, see <a href="https://msdn.microsoft.com/library/bb246060(v=bts.80)">Known Issues for the WCF Adapters</a>.</td>
</tr>
<tr class="odd">
<td><strong>Get</strong></td>
<td>Get the metadata document from the URL specified in the <strong>Metadata Address (URL)</strong> text box. After reviewing the metadata document, click <strong>Next</strong> to continue.</td>
</tr>
</tbody>
</table>


## Metadata Files Page

Use this page to specify metadata files to import.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Metadata Files</strong></td>
<td>Display the metadata files to import.</td>
</tr>
<tr class="even">
<td><strong>Add</strong></td>
<td>Add the metadata files to import to the <strong>Metadata Files</strong> view. This opens the <strong>Add metadata files</strong> dialog box in which you can search disk locations for metadata files. Select a complete set of WSDL and XSD files to use for metadata. You can generate these metadata files as follows:<br />
<br />
svcutil.exe /t:metadata http://localhost/service.svc/mex</td>
</tr>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Remove the metadata file selected in the <strong>Metadata Files</strong> view.</td>
</tr>
</tbody>
</table>


## Import WCF Service Metadata Summary Page

Use this page to review your settings. Click **Back** to make any changes to the WCF service to consume. Click **Import** to create the BizTalk artifacts to be used for consuming the WCF service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Namespace</strong></td>
<td>Specify the namespace of the managed types for the metadata files to import. This namespace appears in the orchestration and schema files that this wizard creates.<br />
<br />
The default value is the name of the BizTalk project in which the BizTalk artifacts are created.</td>
</tr>
</tbody>
</table>


## Completing the BizTalk WCF Service Consuming Wizard Page

Use this page to determine if you have successfully generated the BizTalk artifacts for consuming the WCF service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Run this wizard again</strong></td>
<td>Specify whether to run this wizard again.</td>
</tr>
</tbody>
</table>


## See Also

[How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service](https://msdn.microsoft.com/library/bb226552\(v=bts.80\))  
[Considerations When Consuming WCF Services with the WCF Send Adapters](https://msdn.microsoft.com/library/bb226398\(v=bts.80\))

