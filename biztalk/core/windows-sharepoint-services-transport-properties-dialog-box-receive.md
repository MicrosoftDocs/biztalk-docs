---
title: "Windows SharePoint Services Transport Properties Dialog Box, Receive | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.sharepoint.props.receive"
helpviewer_keywords: 
  - "Windows SharePoint Service adapter, properties"
  - "properties, Windows SharePoint Service adapter"
ms.assetid: dc147c06-30fd-4346-a467-36635fbf70af
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows SharePoint Services Transport Properties Dialog Box, Receive
Use the **Windows SharePoint Transport Properties**dialog box to configure the receive location for the Windows SharePoint Services adapter.  
  
## UIElement List  
 **Adapter Web Service Port**  
 The HTTP port of the IIS Web site where the Windows SharePoint Services adapter Web service is installed. By default, this is the Default Web Site configured on port 80. If you have configured the Windows SharePoint Services Web service on any other IIS Web site than the Default Web Site, you will have to update this value.  
  
 **Timeout**  
 The time-out, in milliseconds, for the adapter runtime Web service calls made to the Windows SharePoint Services adapter Web service. You may need to increase this value if the message or batch size is higher than the average that is expected by the adapter.  
  
 **Archive Filename**  
 (Optional) The archived file Windows SharePoint Services file name. You can type in a literal value like 'PurchaseOrder0001.xml' or an expression. Expressions can include any mix of literals, placeholders and XPATH queries. For example, "PurchOrd-%XPATH='//po:PurchaseOrderId'%-%MessageID%.xml". When no file name is supplied the file name of the source file is used. For more information about expressions, see the appropriate topics in See Also.  
  
 **Archive Location URL**  
 This is the Windows SharePoint Services folder URL, relative to the SharePoint site, where the processed files are archived. For example, Archive or /Shared Documents/Processed Orders/. If an archive location is not specified, the document is deleted after being processed by the adapter.  
  
 **Archive Overwrite**  
 Determines whether existing files in the archive are overwritten. Select 'Yes' to overwrite existing files. Select 'No' to rename the file if a file with the same name already exists in the archive.  
  
 **Batch Size**  
 The maximum number of documents that the Windows SharePoint Services Messaging Adapter Web service will process as a batch. A processed batch might contain fewer messages than the defined batch size; however, it will never contain more messages.  
  
 **Error Threshold**  
 This is the maximum number of consecutive polling failures encountered by the adapter until the receive location is disabled.  
  
 **Namespace Aliases**  
 (Optional) A comma or semi-colon delimited list of namespace alias definitions. Use this field to define the namespace aliases that are used by the XPATH queries introduced in the 'Archive Filename' field. For example, po='http://OrderProcess/POrder', conf='http://OrderProcess/Confirmation' xmlns=""; ipsol='{D8217CF1-4EF7-4bb5-A30D-765ECB09E0D9}'  
  
 **Polling Interval**  
 The time interval, in seconds, between two consecutive queries performed by the adapter to see if any new messages are available for processing.  
  
> [!NOTE]
>  Specifying a lower value improves the throughput and response time for the adapter.  
  
 **SharePoint Site URL**  
 The complete URL of the Windows SharePoint Services Web site. For example, http://BizTalkServer/sites/TestSite.  
  
 **Source Document Library**  
 This is the name of the Windows SharePoint Services document library where the documents are retrieved. For example, Shared Documents or Outbox.  
  
> [!NOTE]
>  You cannot receive messages from a SharePoint list.  
  
 **View Name**  
 This is the Windows SharePoint Services view used to filter documents processed by the adapter. For example, Approved Orders. Leave this field empty to process all the existing documents in the source document library. Folders showing up in a view and the messages contained in those folders will not be processed by the adapter. You can create flat views that will show all documents in a flat structure including documents existing in subfolders.  
  
> [!NOTE]
>  All messages in a flat view will be processed.  
  
 **Microsoft Office Integration**  
 'Optional' to attempt to remove InfoPath processing instructions if possible or process as-is if not (for instance, a binary document), 'Yes' to remove InfoPath processing instructions or skip the message in case of an error, 'No' to process the document 'as-is'.  
  
## See Also  
 [Configuring the Windows SharePoint Services Adapter](../core/configuring-the-windows-sharepoint-services-adapter.md)   
 [Windows SharePoint Services Adapter Expressions](../core/windows-sharepoint-services-adapter-expressions.md)