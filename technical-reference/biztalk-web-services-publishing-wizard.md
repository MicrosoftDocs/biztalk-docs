---
description: "Learn more about: BizTalk Web Services Publishing Wizard"
title: BizTalk Web Services Publishing Wizard
TOCTitle: BizTalk Web Services Publishing Wizard
ms:assetid: 44e7419f-a39f-4d15-867a-60bcedf4d2fb
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559849(v=BTS.80)
ms:contentKeyID: 51527646
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.webservices
---

# BizTalk Web Services Publishing Wizard

 

Use the **BizTalk Web Services Publishing Wizard** to create and publish BizTalk orchestrations as Web services, and to publish schemas as Web services. For general usage information about the BizTalk Web Services Publishing Wizard, see [Using Web Services](https://msdn.microsoft.com/library/aa577881\(v=bts.80\)).

## Create Web Services page

Use this page to select a method of creating your Web service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Publish BizTalk orchestrations as web services</strong></td>
<td>Publish a Web service based on selected orchestrations and Web ports in a BizTalk assembly.</td>
</tr>
<tr class="even">
<td><strong>Publish schemas as web services</strong></td>
<td>Define Web methods and messages of a Web service using selected schemas from BizTalk assemblies as request and/or response message parts.</td>
</tr>
</tbody>
</table>


## BizTalk Assembly page

Use this page to select a BizTalk assembly to publish a Web service from.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>BizTalk assembly file (*.dll)</strong></td>
<td>Select a BizTalk assembly.</td>
</tr>
</tbody>
</table>


Your assembly does not need to be deployed to publish a Web service.

If your assembly has dependencies, you must resolve any dependencies in your assembly before you can publish a Web service from it. The assembly must be deployed and properly bound to be used at runtime.

## Orchestrations and Ports page

You can select the orchestrations and ports in the assembly to expose in your published Web service. Only public ports are visible.

Select the orchestrations and ports that you want to export.

## Web Service Properties page

Use this page to specify the properties for the Web service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Target namespace of web service</strong></td>
<td>Select a target namespace of a Web service. The target namespace appears in the Web Service Description Language (WSDL) file. The <strong>System.Uri</strong> constructor is used to determine the validity.</td>
</tr>
<tr class="even">
<td><strong>Add additional SOAP headers</strong></td>
<td>Add schemas from BizTalk assemblies to use as request and response SOAP headers.</td>
</tr>
<tr class="odd">
<td><strong>Support unknown SOAP headers</strong></td>
<td>Add support for unknown headers.</td>
</tr>
<tr class="even">
<td><strong>Add SharePoint Portal Server 2003 Single Sign-On support</strong></td>
<td>Add support for Single Sign-On (SSO) in SharePoint Portal Server 2003.</td>
</tr>
</tbody>
</table>


You can click the **Advanced** button to control advanced properties that control message format and message processing behavior.

## Web Service Advanced Properties Page

Use this page to customize global web service and web method attributes.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Soap Parameter Style</strong></td>
<td>Specify how parameters are formatted in a SOAP message. Options include:<br />
<br />
- <strong>Bare</strong>: Parameters sent to and from an XML Web service method are placed in the XML elements directly following the <strong>Body</strong> element of a SOAP request or SOAP response.<br />
- <strong>Wrapped (Default)</strong>: Parameters sent to and from an XML Web service method are encapsulated within a single XML element following the <strong>Body</strong> element of the XML portion of a SOAP request or SOAP response.</td>
</tr>
<tr class="even">
<td><strong>Conformance Claims</strong></td>
<td>Specify the web services interoperability (WSI) business process 1.1 (BP1.1) conformance claims made by the web service. <strong>Note:</strong>  BizTalk Server cannot consume web services using BP1.1 conformance claims. If you will be consuming the service from BTS2004, do not use conformance claims.</td>
</tr>
<tr class="odd">
<td><strong>Force Request Response</strong></td>
<td>Specify that one-way BizTalk operations should be exposed as request-response web methods.</td>
</tr>
</tbody>
</table>


## Web Service Project page

Use this page to customize your published Web service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Project name</strong></td>
<td>Enter a project name.</td>
</tr>
<tr class="even">
<td><strong>Project location</strong></td>
<td>Specify the path name of the virtual directory where the Web service is published. <strong>Important:</strong> You must use ANSI characters.</td>
</tr>
<tr class="odd">
<td><strong>Overwrite existing project</strong></td>
<td>Overwrite the existing project when you republish a Web service.</td>
</tr>
<tr class="even">
<td><strong>Browse button</strong></td>
<td>Search disk locations for a file location.</td>
</tr>
<tr class="odd">
<td><strong>Allow anonymous access to web service</strong></td>
<td>Sets the <strong>AuthAnonymous</strong> flag on the published virtual directory. This flag is useful in a development environment.</td>
</tr>
<tr class="even">
<td><strong>Create BizTalk Receive locations</strong></td>
<td>Generates a BindingInfo.xml binding file to create the receive locations that correspond to the published Web service.<br />
<br />
The BindingInfo.xml file can be imported by the development command-line tool or wizard to create the necessary receive locations. You can find BindingInfo.xml in the temp folder of the published Web service's virtual directory.</td>
</tr>
</tbody>
</table>


## Request SOAP Headers/Response SOAP Headers page

Use this page to add and remove schemas from BizTalk assemblies to use as request and response SOAP headers.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Add</strong> button</td>
<td>Add a schema by specifying the path name to a BizTalk assembly that contains document schemas.</td>
</tr>
<tr class="even">
<td><strong>Remove</strong> button</td>
<td>Remove a schema.</td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>Top-level elements of ComplexType elements are listed and can be used as SOAP headers.</P>



Use these pages to select one or more schema types from BizTalk assemblies to use as request and response SOAP headers.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>BizTalk assembly file (*.dll)</strong></td>
<td>Select a BizTalk assembly.</td>
</tr>
<tr class="even">
<td><strong>Browse</strong> button</td>
<td>Search disk locations for a file location.</td>
</tr>
</tbody>
</table>


## Web Service page

Use this page to describe the Web service that you are creating.

Right-click a node to view properties and menu options to add, rename, or delete a Web service or Web method.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Add web service</strong></td>
<td>Add a Web service.</td>
</tr>
<tr class="even">
<td><strong>Rename web service description</strong></td>
<td>Rename a Web service. Type a new name for your Web service.</td>
</tr>
<tr class="odd">
<td><strong>Add web method</strong></td>
<td>Add a one-way Web method.<br />
<br />
Add a request-response Web method.</td>
</tr>
<tr class="even">
<td><strong>Select schema type</strong></td>
<td>Select a schema type in <strong>Request Message Type/Request Message Type</strong> page.</td>
</tr>
<tr class="odd">
<td><strong>Rename web message part</strong></td>
<td>Rename the Web message part.</td>
</tr>
</tbody>
</table>


## Request Message Type/Response Message Type page

Use these pages to select one or more schema types from BizTalk assemblies to use as request and response SOAP headers.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>BizTalk assembly file (*.dll)</strong></td>
<td>Select a BizTalk assembly.</td>
</tr>
<tr class="even">
<td><strong>Browse</strong> button</td>
<td>Search disk locations for a file location.</td>
</tr>
</tbody>
</table>


## Web Service Project Summary page

Use this page to review your settings. Click **Back** to make any changes to your published Web service. Click **Create** to create your published Web service.

## Completing the Web Services Publishing Wizard page

Use this page to determine if you have successfully published your Web service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>link to published Web service</strong></td>
<td>Go to your published Web service project.</td>
</tr>
</tbody>
</table>


## See Also

[How to Use the BizTalk Web Services Publishing Wizard to Publish an Orchestration as a Web Service](https://msdn.microsoft.com/library/aa578703\(v=bts.80\))  
[How to Use the BizTalk Web Services Publishing Wizard to Publish Schemas as a Web Service](https://msdn.microsoft.com/library/aa578158\(v=bts.80\))  
[Considerations When Publishing Web Services](https://msdn.microsoft.com/library/aa559660\(v=bts.80\))

