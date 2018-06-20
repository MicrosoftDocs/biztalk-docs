---
title: "Windows SharePoint Services 4.0 Support | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 84be7aa0-2ff2-4e40-9c39-5cb89549c636
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows SharePoint Services 4.0 Support
The Windows SharePoint Services adapter for BizTalk Server provides feature/functionality parity with the Windows SharePoint Services adapter for [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]. The Windows SharePoint Services adapter for BizTalk Server also supports the following functionality available with Windows SharePoint Services 4.0:  

- Sending messages to a Windows SharePoint Services 4.0 blog site.  

- Sending messages to and receiving message from a Windows SharePoint Services 4.0 Wiki site.  

  The Windows SharePoint Services adapter for BizTalk Server does not provide support for the following features that are available in Windows SharePoint Services 4.0:  

- **Recycle Bin**: The Windows SharePoint Services adapter for BizTalk Server adapter does not support receiving, or explicitly sending messages from/to the Recycle Bin.  

- **Lists folders**: The Windows SharePoint Services adapter for BizTalk Server can send messages to lists but it cannot receive messages from lists. Windows SharePoint Services 4.0 supports folders in lists but the Windows SharePoint Services adapter for BizTalk Server does not support this feature. Therefore, the Windows SharePoint Services adapter for BizTalk Server cannot create list items in a list folder other than the root folder.  

- The following sections describe in greater detail how to use the Windows SharePoint Services adapter for BizTalk Server to send messages to a Windows SharePoint Services 4.0 blog site and how to send messages to and receive messages from a Windows SharePoint Services 4.0 Wiki site.  

## Sending to a Windows SharePoint Services 4.0 Blog Site  
 In a Windows SharePoint Services 4.0 blog site, posts are stored in the **Posts** list and post categories are defined in the **Categories** list.  

 To post a message to a Windows SharePoint Services 4.0 blog site, enter the following values in the adapter **Transport Properties** dialog box when configuring a send port that uses the Windows SharePoint Services adapter:  


|        Property        |                                                                                            Value                                                                                            |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Destination Folder URL |                                            Destination folder URL of the Posts list, relative to the SharePoint site, for example "Lists/Posts".                                            |
|  SharePoint Site URL   | URL of the Windows SharePoint Services 4.0 blog site, for example http://<em>\<servername\></em>/sites/blog/ where *\<servername\>* is a placeholder for the actual name of the Web server. |

 Then set the values for the **Category**, **Published**, **Title**, and **Body** properties for the blog posting by setting corresponding values in the WSS.ConfigPropertiesXml context property of the message. This can be done with a custom pipeline or in an orchestration. For example, the following expression in an orchestration would set values in the WSS.ConfigPropertiesXml context property of the Message_Out message.  

```  
int_Category = 1;  
str_Published = Microsoft.SharePoint.Utilities.SPUtility.CreateISO8601DateTimeFromSystemDateTime(System.DateTime.Now);  
// requires a reference to Microsoft.SharePoint.dll  
str_Title = "This is the title of the post from the WSS adapter";  
str_Body = "This is the body of the post from the WSS adapter";  

Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Category</PropertyName1>  
<PropertySource1>” + int_Category + “</PropertySource1>  
<PropertyName2>Published</PropertyName2>  
<PropertySource2>” + str_Published + “</PropertySource2>  
<PropertyName3>Title</PropertyName3>  
<PropertySource3>” + str_Title + “</PropertySource3>  
<PropertyName4>Body</PropertyName4>  
<PropertySource4>” + str_Body + “</PropertySource4>  
</ConfigPropertiesXml>”;  
```  

 The variables in this expression would use the following types:  

|Variable name|Type|  
|-------------------|----------|  
|int_Category|System.Int32|  
|str_Published|System.String|  
|str_Title|System.String|  
|str_Body|System.String|  

 A post created this way will be set to a state of **not approved**, which will require approval by the blog owner before it is visible on the site.  

 The supported column types for the list can be viewed on the settings page for the list. For more information about the Windows SharePoint Services column types that are supported by the Windows SharePoint Services adapter, see [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md).  

## Sending to and Receiving from a Windows SharePoint Services 4.0 Wiki Document Library  
 In a Windows SharePoint Services 4.0 site, a Wiki site uses the **Wiki Pages** document library. The Wiki Pages document library stores the text of the Wiki page in a **Wiki Content** column which uses a UI type of **Multiple lines of text**. The **Multiple lines of text** UI type correlates to the **SPFieldType.Note** SharePoint object model type. For more information about the Windows SharePoint Services column types that are supported by the Windows SharePoint Services adapter see [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md).  

### Sending to a Windows SharePoint Services 4.0 Wiki Document Library  
 When sending messages to a Windows SharePoint Services 4.0 Wiki site, the contents of the Wiki page are stored within the Windows SharePoint Services adapter context property named **WSS.ConfigPropertiesXml**. To post a message to a Windows SharePoint Services 4.0 Wiki site, enter the following values in the adapter **Transport Properties** dialog box when configuring a send port that uses the Windows SharePoint Services adapter:  


|        Property        |                                                                                            Value                                                                                            |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Destination Folder URL |                                                   URL of the Wiki site home page, relative to the SharePoint site, for example "wikiSP".                                                    |
|  SharePoint Site URL   | URL of the Windows SharePoint Services 4.0 Wiki site, for example http://<em>\<servername\></em>/sites/wiki/ where *\<servername\>* is a placeholder for the actual name of the web server. |

 Then set the value for the **Wiki Content** property for the Wiki page by setting the corresponding value in the WSS.ConfigPropertiesXml context property of the message. This can be done with a custom pipeline or in an orchestration. For example, the following expression in an orchestration would set values in the WSS.ConfigPropertiesXml context property of the Message_Out message:  

```  
str_Wiki = "This is a sample Wiki page entry.";  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  

 The str_Wiki variable in this expression would use the **System.String** data type.  

> [!IMPORTANT]
>  The Windows SharePoint Services 4.0 Wiki document library supports versioning, however, the Windows SharePoint Services adapter for BizTalk Server 2010does not support versioning. Therefore, Wiki pages that are updated by the Windows SharePoint Services adapter for BizTalk Server will lose their previous versions. Because of this limitation, a Wiki page that is received by the Windows SharePoint Services adapter for BizTalk Server and archived in a different Wiki document library will preserve only its last version, with all other versions being deleted.  

### Receiving from a Windows SharePoint Services 4.0 Wiki Document Library  
 When receiving messages from a Windows SharePoint Services 4.0 Wiki site, the contents of the Wiki page are stored within the Windows SharePoint Services adapter context property named **WSS.InPropertiesXml**.  

 To receive a message from a Windows SharePoint Services 4.0 Wiki page, enter the following values in the adapter **Transport Properties** dialog box when configuring a receive location that uses the Windows SharePoint Services adapter:  

|Property|Value|  
|--------------|-----------|  
|SharePoint Site URL|URL of the Wiki site home page, relative to the SharePoint site, for example "wiki".|  
|Source Document Library URL|URL of the Wiki site home page, relative to the SharePoint site, for example "wikiRL".|  

 Then retrieve the wiki page contents from the **Wiki Content** node of the **WSS.InPropertiesXml** context property of the received message. This can be done with a custom pipeline or in an orchestration. For example, in the following orchestration expression, the **str_Wiki** variable is populated with the value of the **Wiki Content** node from the **WSS.InPropertiesXml** context property of the **Message_In** message. Then, the **Wiki Content** property of the **WSS.ConfigPropertiesXml** context property of the **Message_Out** message is set to the value of the **str_Wiki** variable:  

```  
str_PropertiesXml = Message_In(WSS.InPropertiesXml);  
doc = doc.LoadXml(str_PropertiesXml);  
node = doc.SelectSingleNode("InPropertiesXml/Property[@name='Wiki Content']);  
str_Wiki = node.InnerText;  
Message_Out(WSS.ConfigPropertiesXml) = “<ConfigPropertiesXml>  
<PropertyName1>Wiki Content</PropertyName1>  
<PropertySource1>” + str_Wiki + “</PropertySource1>  
</ConfigPropertiesXml>”;  
```  

 The variables in this expression would use the following types:  

|Variable name|Type|  
|-------------------|----------|  
|str_PropertiesXml|System.Xml.XmlDocument|  
|doc|System.Xml.XmlDocument|  
|node|System.Xml.XmlNode|  
|str_Wiki|System.String|  

## See Also  
 [Windows SharePoint Services Adapter](../core/windows-sharepoint-services-adapter.md)