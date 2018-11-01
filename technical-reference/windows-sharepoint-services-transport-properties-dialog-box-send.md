---
title: Windows SharePoint Services Transport Properties Dialog Box, Send
TOCTitle: Windows SharePoint Services Transport Properties Dialog Box, Send
ms:assetid: e3328fb9-03c0-426e-8ca6-824e07f3fe8a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561575(v=BTS.80)
ms:contentKeyID: 51532975
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.sharepoint.props.send
---

# Windows SharePoint Services Transport Properties Dialog Box, Send

 

Use the **Windows SharePoint Transport Properties**dialog box to configure the send port for the Windows SharePoint Services adapter.

## UIElement List

**Adapter Web Service Port**  
The HTTP port of the IIS Web site where the Windows SharePoint Services adapter Web service is installed. By default, this is the Default Web Site configured on port 80. If you have configured the Windows SharePoint Services Web service on any other IIS Web site than the Default Web Site, you will have to update this value.

**Timeout**  
The time-out, in milliseconds, for the adapter runtime Web service calls made to the Windows SharePoint Services adapter Web service. You may need to increase this value if the message or batch size is higher than the average that is expected by the adapter.

**Destination Folder URL**  
The Windows SharePoint Services destination folder URL, relative to the SharePoint site. For example, Shared Documents, Shared Documents/Purchase Orders/, or Lists/Tasks. You can send messages to a SharePoint list by specifying the URL of the list, for example, Lists/Tasks. If you specify a list as a destination, the message body will not be saved with the list item but the values extracted from the message will still be promoted into the SharePoint columns.


> [!NOTE]
> <P>Sometimes the SharePoint document library, list, or folder URL is different from the name of that item. Check the address bar in Internet Explorer to discover the correct URL.</P>



**Filename**  
(Optional) The Windows SharePoint Services file name. You can type in a literal value like 'PurchaseOrder0001.xml' or an expression. Expressions can include any mix of literals, placeholders and XPATH queries, for example: "PurchOrd-%XPATH='//po:PurchaseOrderId'%-%MessageID%.xml". When no file name is supplied, the value supplied by the orchestration is used or 'Msg-%MessageID%.xml' if the orchestration does not define the file name. For more information about expressions, see the appropriate topics in See Also.

**Namespaces Aliases**  
(Optional) A comma or semi-colon delimited list of namespace alias definitions. Use this field to define the namespace aliases that are used by the XPATH queries introduced in fields like 'Filename' or 'Column Value'. For example, po='http://OrderProcess/POrder', conf='http://OrderProcess/Confirmation' ; ipsol='{D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}'.


> [!NOTE]
> <P>This property does not override the WSS.ConfigNamespacesAliases message context property defined by the orchestration. The two values are merged instead.</P>



**Overwrite**  
Determines whether an existing file is overwritten. Select 'Yes' to overwrite existing files. Select 'No' to raise an error and suspend the message when a file with the same name already exists. Select 'Orchestration' to use the value defined by the orchestration.

**SharePoint Site URL**  
The complete URL of the Windows SharePoint Services Web site. For example, http://BizTalkServer/sites/TestSite.

**Microsoft Office Integration**  
'Optional' to change the document so that it automatically opens in an Office application like InfoPath or save the document as-is if no InfoPath solution is found, 'Yes' to change the document so that it automatically opens in an Office application like InfoPath or suspend the message if no InfoPath solution is found, 'No' to save the document 'as-is' without any changes, 'Orchestration' to use the value defined by the orchestration.


> [!NOTE]
> <P>At least one of the property pairs Templates Document Library and Templates Namespace Column or Templates Fallback Document Library and Templates Fallback Namespace Column is required when Microsoft Office Integration is set to Yes.</P>



**Templates Document Library**  
Enter the name of a SharePoint document library where the InfoPath solutions are stored. For example, Shared Documents. This is the first place where the adapter will look for a matching InfoPath solution. If a solution is not found, the adapter will look in the Templates fallback document library.


> [!NOTE]
> <P>This field is required when the Templates Namespace Column field is not empty.</P>



**Templates Fallback Document Library**  
Enter the name of a SharePoint document library where the InfoPath solutions are stored. For example, Templates. The adapter will only search this document library for a matching InfoPath solution if a solution is not found in the Custom templates document library.


> [!NOTE]
> <P>This field is required when the Templates Fallback Namespace Column field is not empty.</P>



**Templates Fallback Namespace Column**  
This is the name of the SharePoint column that stores the namespace of the InfoPath solution. For example, Namespace.


> [!NOTE]
> <P>This field is required when the Templates Document Library field is not empty.</P>




> [!NOTE]
> <P>This field is case-sensitive.</P>



**Templates Namespace Column**  
This is the name of the SharePoint column that stores the namespace of the InfoPath solution. For example, Namespace.


> [!NOTE]
> <P>This field is required when the Templates Document Library field is not empty.</P>




> [!NOTE]
> <P>This field is case-sensitive.</P>



**Column n**  
This is the name of the Windows SharePoint Services column that exists in the destination document library. This is the column that should be updated with the value extracted from the message or specified in the 'Column value' field.


> [!NOTE]
> <P>You can specify up to 16 columns.</P>




> [!NOTE]
> <P>This field is case-sensitive.</P>



**Column n Value**  
Enter the column value to be set for this message. You can type in a literal value like 'Purchase Order' or an expression. Expressions can include any mix of literals, placeholders, and XPATH queries. For example, "%XPATH='//po:POAmount'%", "%SendingOrchestrationID%".


> [!NOTE]
> <P>You can specify up to 16 column values.</P>



## See Also

[Configuring the Windows SharePoint Services Adapter](https://msdn.microsoft.com/en-us/library/aa560619\(v=bts.80\))

