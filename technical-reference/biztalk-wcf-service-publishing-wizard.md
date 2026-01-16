---
description: "Learn more about: BizTalk WCF Service Publishing Wizard"
title: BizTalk WCF Service Publishing Wizard
TOCTitle: BizTalk WCF Service Publishing Wizard
ms:assetid: d2cdd4d6-af92-447d-959a-6eff26c7db37
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226547(v=BTS.80)
ms:contentKeyID: 51531446
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.wcf-service,publishing.wizard
ms.topic: ui-reference
---

# BizTalk WCF Service Publishing Wizard

 

Use the BizTalk WCF Service Publishing Wizard to create and publish BizTalk orchestrations as WCF services, and to publish schemas as WCF services for the isolated WCF adapters hosted by Web applications running in IIS. You can also use the BizTalk WCF Service Publishing Wizard to publish service metadata for any WCF locations for the in-process WCF adapters. For general usage information about the BizTalk WCF Service Publishing Wizard, see [Using WCF Services](https://msdn.microsoft.com/library/bb246032\(v=bts.80\)).


> [!NOTE]
> <P>When running the BizTalk WCF Service Publishing Wizard on a Windows operating system that uses User Access Control (UAC), such a Windows Server 2008 SP2 and Windows 7, you may need to disable UAC to run the wizard to completion. This can be done through the MSCONFIG.EXE system utility.</P>




> [!NOTE]
> <P>You may need to register the .svc extension with Internet Information Server (IIS) before you are able to browse to the service using the <STRONG>WCF Service Location Page</STRONG>. You can find information on this topic at either <A href="/dotnet/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service">Deploying an Internet Information Services-Hosted WCF Service</A> or <A href="/previous-versions/dotnet/netframework-3.0/aa751792(v=vs.85)">Deploying an IIS-Hosted WCF Service</A>.</P>



## WCF Service Type

Use this page to select the type of WCF service to publish.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Service endpoint</strong></td>
<td>Publish the WCF services based on selected BizTalk orchestrations or schemas in a BizTalk assembly.</td>
</tr>
<tr class="even">
<td><strong>Adapter name (Transport type)</strong></td>
<td>Specify the WCF adapter with which to publish these WCF services. Valid values only include the isolated WCF receive adapters as the following:<br />
<br />
- <strong>WCF-BasicHttp</strong><br />
- <strong>WCF-WSHttp</strong><br />
- <strong>WCF-CustomIsolated</strong><br />
<br />
You have to republish the WCF services if you want to change this adapter type.</td>
</tr>
<tr class="odd">
<td><strong>Enable metadata endpoint</strong></td>
<td>Indicate whether the isolated WCF receive location hosted by Internet Information Services (IIS) publish service metadata for retrieval using an HTTP/GET request. By enabling this check-box, the wizard generates Web.config where the <strong>httpGetEnabled</strong> attribute of the <strong>&lt;serviceMetadata&gt;</strong> element is set to <strong>true</strong>. You can use a metadata import tool (such as SvcUtil.exe) to generate the client code required to call this service in the development environment. To prevent unintentional disclosure of potentially sensitive service metadata, it is recommended to disable this behavior on the production environment.</td>
</tr>
<tr class="even">
<td><strong>Create BizTalk receive locations in the following application</strong></td>
<td>Specify whether to create the receive locations for the WCF services in the BizTalk application specified in the <strong>BizTalk application name</strong> property.</td>
</tr>
<tr class="odd">
<td><strong>BizTalk application name</strong></td>
<td>Specify the BizTalk application where the receive locations for the WCF services are created.</td>
</tr>
<tr class="even">
<td><strong>Metadata only endpoint (MEX)</strong></td>
<td>Use this option for to publish service metadata of the existing WCF receive locations for retrieval using an HTTP/GET request. By using this option, you can publish service metadata of an in-process WCF receive adapter through IIS. By enabling this option, the wizard generates Web.config where the <strong>httpGetEnabled</strong> attribute of the <strong>&lt;serviceMetadata&gt;</strong> element is set to <strong>true</strong>. You can use a metadata import tool (such as SvcUtil.exe) to generate the client code required to call this service in the development environment. To prevent unintentional disclosure of potentially sensitive service metadata, it is recommended to disable this behavior on the production environment. <strong>Note:</strong> When you select the Metadata only endpoint (MEX), make sure not to leave the Publish metadata for receive location drop-down list blank.</td>
</tr>
<tr class="odd">
<td><strong>Publish metadata for receive location</strong></td>
<td>Specify the WCF receive location for which to publish service metadata through IIS.</td>
</tr>
</tbody>
</table>


## Create WCF Service Page

Use this page to select a method of creating your WCF service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Publish BizTalk orchestrations as WCF service</strong></td>
<td>Publish WCF services based on selected orchestrations and ports in a BizTalk assembly.</td>
</tr>
<tr class="even">
<td><strong>Publish schemas as WCF service</strong></td>
<td>Publish WCF services by specifying operations and messages of WCF services using selected schemas from BizTalk assemblies as request and/or response message parts.</td>
</tr>
</tbody>
</table>


## BizTalk Assembly Page

Use this page to select a BizTalk assembly to publish WCF services from.

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


Your assembly does not need to be deployed to publish WCF services at design time.

If your assembly has dependencies, you must resolve any dependencies in your assembly before you can publish WCF services from it. The assembly must be deployed and properly bound to be used at run time.

## Orchestrations and Ports Page

Use this page to select orchestrations and ports to publish in WCF services.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>BizTalk assembly description</strong></td>
<td>Select the orchestrations and ports that you want to export. You can select the orchestrations and ports in the assembly to expose in your published WCF services. Only public ports are visible.</td>
</tr>
<tr class="even">
<td><strong>Merge all selected ports into a single WCF service</strong></td>
<td>Specify whether to merge all the selected ports into a single WCF service. If this check box is cleared, one service can have only one port, which can result in multiple services being generated. <strong>Note:</strong> If you select this check box, all operations in a single WCF service must have unique names in the service.<br />
<br />
The default value is cleared.</td>
</tr>
</tbody>
</table>


## WCF Service Properties Page

Use this page to specify the properties for the WCF services.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Target namespace of WCF service</strong></td>
<td>Select a target namespace of the WCF services. The target namespace appears in the Web Services Description Language (WSDL) file. The <strong>System.Uri</strong> constructor is used to determine the validity of this namespace.</td>
</tr>
</tbody>
</table>


## WCF Service Location Page

Use this page to specify the location of the WCF services to create.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Location (http://host[:port]/path)</strong></td>
<td>Specify the path name of the virtual directory where the WCF services are published. <strong>Important:</strong> You must use ANSI characters.</td>
</tr>
<tr class="even">
<td><strong>Overwrite existing location</strong></td>
<td>Overwrite the existing location when you republish the WCF services.</td>
</tr>
<tr class="odd">
<td><strong>Browse button</strong></td>
<td>Search the virtual directory for the WCF services.</td>
</tr>
<tr class="even">
<td><strong>Allow anonymous access to WCF service</strong></td>
<td>Set the <strong>AuthAnonymous</strong>flag on the published virtual directory.</td>
</tr>
</tbody>
</table>


## WCF Service Page

Use this page to describe the WCF service that you are creating. Right-click a node to view properties and menu options to add, rename, or delete a WCF service or Web method.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Web service description</strong></td>
<td>Display the detail information about the WCF services published. When you click a node in this tree view, the <strong>Information</strong> text box displays more detail information about the node.<br />
<br />
The default value is <strong>BizTalkWcfService</strong>.</td>
</tr>
<tr class="even">
<td><strong>Information</strong></td>
<td>Display more detail information about the node selected in the <strong>Web service description</strong> view.</td>
</tr>
<tr class="odd">
<td><strong>Add web service</strong></td>
<td>Add a WCF service. To run this command, right-click the Web service description name, and then click <strong>Add web service</strong>.</td>
</tr>
<tr class="even">
<td><strong>Rename web service description</strong></td>
<td>Rename a Web service description. To run this command, right-click the Web service description name, and then click <strong>Rename web service description</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Add web method</strong></td>
<td>Add a Web method in the WCF service selected in the <strong>Web service description</strong> view. To run this command, right-click a WCF service, click <strong>Add web method</strong>, and then click the message exchange pattern for the Web method: <strong>One-way</strong> or <strong>Request-response</strong>.</td>
</tr>
<tr class="even">
<td><strong>Rename web service</strong></td>
<td>Rename the WCF service selected in the <strong>Web service description</strong> view. To run this command, right-click a WCF service, and then click <strong>Rename web service</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Delete web service</strong></td>
<td>Delete the WCF service selected in the <strong>Web service description</strong> view. To run this command, right-click a WCF service, and then click <strong>Delete web service</strong>.</td>
</tr>
<tr class="even">
<td><strong>Rename web method</strong></td>
<td>Rename the Web method selected in the <strong>Web service description</strong> view. To run this command, right-click a Web method, and then click <strong>Rename web method</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Delete web method</strong></td>
<td>Delete the Web method selected in the <strong>Web service description</strong> view. To run this command, right-click a Web method, and then click <strong>Delete web method</strong>.</td>
</tr>
<tr class="even">
<td><strong>Select schema type</strong></td>
<td>Select a schema type in the <strong>Request Message Type</strong> or <strong>Response Message Type</strong> dialog box. To run this command, right-click a WCF message, and then click <strong>Select schema type</strong>. This command opens the <strong>Request Message Type</strong> or <strong>Response Message Type</strong> dialog box depending on the direction of the selected WCF message: <strong>Input</strong> or <strong>Output</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Rename web message</strong></td>
<td>Rename the WCF message selected in the <strong>Web service description</strong> view. To run this command, right-click a WCF message, and then click <strong>Rename web message</strong>.</td>
</tr>
</tbody>
</table>


### Request Message Type/Response Message Type

Use these dialog boxes to select a message type from BizTalk assemblies to use as a request or response WCF message.

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
<td><strong>Browse</strong></td>
<td>Search disk locations for a file location.</td>
</tr>
<tr class="odd">
<td><strong>Available schema types</strong></td>
<td>Display the message types included in the BizTalk assembly selected in the <strong>BizTalk assembly file (*.dll)</strong> property. You can select a message type to use as a request or response WCF message.</td>
</tr>
</tbody>
</table>


## WCF Service Summary Page

Use this page to review your settings. Click **Back** to make any changes to your published WCF services. Click **Create** to create your published WCF services.

## Completing the BizTalk WCF Service Publishing Wizard Page

Use this page to determine if you have successfully published your WCF service.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Run this wizard, click Finish</strong></td>
<td>Specify whether to run this wizard again.</td>
</tr>
</tbody>
</table>


## See Also

[Considerations When Publishing WCF Services with the WCF Receive Adapters](https://msdn.microsoft.com/library/bb226362\(v=bts.80\))  
[How to Use the BizTalk WCF Service Publishing Wizard to Publish Orchestrations as WCF Services](https://msdn.microsoft.com/library/bb226564\(v=bts.80\))  
[How to Use the BizTalk WCF Service Publishing Wizard to Publish Schemas as WCF Services](https://msdn.microsoft.com/library/bb246047\(v=bts.80\))  
[Walkthrough: Publishing WCF Services with the WCF-BasicHttp Adapter](https://msdn.microsoft.com/library/bb246063\(v=bts.80\))  
[Walkthrough: Publishing WCF Services with the WCF-NetMsmq Adapter](https://msdn.microsoft.com/library/bb259950\(v=bts.80\))