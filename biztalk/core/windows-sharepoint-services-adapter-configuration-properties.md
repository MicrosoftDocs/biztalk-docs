---
description: "Learn more about: Windows Sharepoint Services Adapter Configuration Properties"
title: "Windows Sharepoint Services Adapter Configuration Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Windows Sharepoint Services Adapter Configuration Properties
The following table lists the configuration properties that you can set for a Windows Sharepoint Services adapter receive location:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|SiteUrl|VT_BSTR|Specify the complete URL of the Windows SharePoint Services Web site.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
|WssLocation|VT_BSTR|Specify the URL of the Windows SharePoint Services document library, relative to the SharePoint site, where the documents are retrieved.|You cannot receive messages from a SharePoint list or folder.|Sometimes the SharePoint document library is different from the name of that item. Check the address bar in Internet Explorer to discover the correct URL.|  
|ViewName|VT_BSTR|Specify the Windows SharePoint Services view used to filter documents processed by the adapter.|None|All messages in a flat view will be processed.|  
|ArchiveLocation|VT_BSTR|Specify the Windows SharePoint Services folder URL, relative to the SharePoint site, where the processed files are archived.|None|Sometimes the SharePoint document library, or folder URL is different from the name of that item. Check the address bar in Internet Explorer to discover the correct URL.|  
|NamespaceAliases|VT_BSTR|Specify a comma or semicolon-delimited list of namespace aliases definitions.|None|None|  
|ArchiveFileName|VT_BSTR|Specify the archived file Windows SharePoint Services file name.|The "%SendingOrchestrationID%" and "%SendingOrchestrationType%" macros are not supported by this field.|None|  
|Overwrite|VT_BSTR|Specify whether existing files in the archive are overwritten.|Valid values are:<br /><br /> -   yes<br />-   no|The default value is no.|  
|ErrorThreshold|VT_BSTR|Specify the maximum number of consecutive polling failures encountered by the adapter until the receive location is disabled.|Valid values are from 0 to 2147483647.|Set this property to 0 in order to never disable the receive location.<br /><br /> The default value is 10.|  
|PollingInterval|VT_BSTR|Specify the time interval, in seconds, between two consecutive queries performed by the adapter to see if any new messages are available for processing.|Valid values are from 1 to 2147483647.|Specifying a lower value improves the throughput and response time for the adapter.<br /><br /> The default value is 60.|  
|BatchSize|VT_BSTR|Specify the maximum number of documents that the Windows SharePoint Services Messaging Adapter Web service will process as a batch.|Valid values are from 1 to 2147483647.|A processed batch might contain fewer messages than the defined batch size; however, it will never contain more messages.<br /><br /> The default value is 20.|  
|OfficeIntegration|VT_BSTR|Specify the level of Office integration.|Valid values are:<br /><br /> -   **optional** - attempt to remove InfoPath processing instructions if possible or to process as is if not possible.<br />-   **no** - process the document "as is."<br />-   **yes** - remove InfoPath processing instructions or skip the message in case of an error.|The default value is optional.|  
|Timeout|VT_BSTR|Specify time-out, in milliseconds, for the adapter runtime Web service calls made to the Windows SharePoint Services adapter Web service.|Valid values are from 1000 to 2147483647.|The default value is 100000.|  
|AdapterWSPort|VT_BSTR|Specify the HTTP port of the IIS Web site where the Windows SharePoint Services adapter Web service is installed.|None|The default value is 80.|  
|uri|VT_BSTR|Specify the full path to the Windows SharePoint Services document library.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
  
 The following code shows the format of the string you use to set the properties:  
  
```  
<CustomProps><AdapterConfig vt="8"><ReceiveLocation xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><SiteUrl>http://BTS2006/sites/BASSite/</SiteUrl><WssLocation>Shared Docs</WssLocation><ViewName>Approved</ViewName><ArchiveLocation>Archive</ArchiveLocation><NamespaceAliases>po='http://POProcess/POrder'</NamespaceAliases><ArchiveFileName>PurchaseOrder0001.xml</ArchiveFileName><Overwrite>no</Overwrite><ErrorThreshold>10</ErrorThreshold><PollingInterval>60</PollingInterval><BatchSize>20</BatchSize><OfficeIntegration>optional</OfficeIntegration><Timeout>100000</Timeout><AdapterWSPort>80</AdapterWSPort><uri>wss://bts2006:80/sites/BASSite/Shared+Docs?ViewName=Approved</uri></ReceiveLocation></AdapterConfig></CustomProps>  
```  
  
 The following table lists the configuration properties that you can set for a Windows Sharepoint Services adapter send port:  
  
|Property name|Type|Description|Restrictions|Comments|  
|-------------------|----------|-----------------|------------------|--------------|  
|SiteUrl|VT_BSTR|Specify the complete URL of the Windows SharePoint Services Web site|The URI for a send port or receive location cannot exceed 256 characters.|None|  
|WssLocation|VT_BSTR|Specify the Windows SharePoint Services destination folder URL, relative to the SharePoint site.|None|Sometimes the SharePoint document library, list, or folder URL is different from the name of that item. Check the address bar in Internet Explorer to find the correct URL.|  
|Overwrite|VT_BSTR|Specify whether to overwrite existing files.|Valid values are:<br /><br /> -   no<br />-   orchestration<br />-   rename<br />-   yes|The default value is no.|  
|NamespaceAliases|VT_BSTR|Specify a comma or semicolon-delimited list of namespace aliases definitions.|None|Use this field to define the namespace aliases that are used by the XPATH queries introduced in fields.<br /><br /> This property does not override the WSS.ConfigNamespacesAliases message context property defined by the orchestration. The two values are merged instead.|  
|FileName|VT_BSTR|Specify the Windows SharePoint Services file name|None|When sending messages to a list, the value specified in the Filename property is ignored and will not be saved in any SharePoint column. SharePoint lists do not have a Filename column. Instead, update the Title column using one of the 16 available columns.|  
|OfficeIntegration|VT_BSTR|Specify to change the document so that it automatically opens in an Office application like InfoPath or to save the document as is if no InfoPath solution is found.|Valid values are:<br /><br /> -   no<br />-   optional<br />-   orchestration<br />-   yes<br />-   yesformlibrary|The default value is optional.|  
|TemplatesDocLib|VT_BSTR|Specify the name of a SharePoint document library where the InfoPath solutions are stored.|This property must contain a value if the TemplatesNamespaceCol property contains a value.|The document library must have at least one SharePoint column of type Single line of text which is populated with the namespace and the root node of the XML documents that can be opened with this InfoPath solution, or just the root node.|  
|TemplatesNamespaceCol|VT_BSTR|Specify the name of the Templates Fallback Document Library SharePoint column that stores the namespace of the InfoPath solution.|This property must contain a value if the TemplatesDocLib property contains a value.<br /><br /> This field is case-sensitive.|None|  
|CustomTemplatesDocLib|VT_BSTR|Specify the name of a SharePoint document library where the InfoPath solutions are stored.|This property must contain a value if the CustomTemplatesNamespaceCol property contains a value.<br /><br /> This field is case-sensitive.|None|  
|CustomTemplatesNamespaceCol|VT_BSTR|Specify the name of the Templates Document Library SharePoint column that stores the namespace of the InfoPath solution.|This property must contain a value if the CustomTemplatesDocLib property contains a value.<br /><br /> This field is case-sensitive.|None|  
|PropertyName(n)|VT_BSTR|Specify the name of the Windows SharePoint Services column that exists in the destination document library.|This field is case-sensitive.|You can specify up to 16 columns.|  
|PropertySource(n)|VT_BSTR|Specify the column value to be set for this message.|None|You can specify up to 16 column values.|  
|Timeout|VT_BSTR|Specify the time-out, in milliseconds, for the adapter runtime Web service calls made to the Windows SharePoint Services adapter Web service.|Valid values are from 1000 to 2147483647.|The default value is 100000.|  
|AdapterWSPort|VT_BSTR|Specify the HTTP port of the IIS Web site where the Windows SharePoint Services adapter Web service is installed.|None|The default value is 80.|  
|uri|VT_BSTR|Specify the full path to the Windows SharePoint Services destination folder URL.|The URI for a send port or receive location cannot exceed 256 characters.|None|  
  
 The following code shows the format of the string you use to set the properties:  
  
> [!NOTE]
>  The definitions for PropertyName2 and PropertySource2 through PropertyName16 and PropertySource16 were omitted from this string.  
  
```  
<CustomProps><AdapterConfig vt="8"><SendPort xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><SiteUrl>http://BizTalkServer/sites/BASSite/</SiteUrl><WssLocation>Shared Documents/Purchase Orders</WssLocation><Overwrite>yes</Overwrite><NamespaceAliases>po='http://OrderProcess/POrder'</NamespaceAliases><FileName>PurchaseOrder0001.xml</FileName><OfficeIntegration>yesformlibrary</OfficeIntegration><TemplatesDocLib>Templates</TemplatesDocLib><TemplatesNamespaceCol>NamespaceFallback</TemplatesNamespaceCol><CustomTemplatesDocLib>Shared Documents</CustomTemplatesDocLib><CustomTemplatesNamespaceCol>Namespace</CustomTemplatesNamespaceCol><PropertyName1>Column1</PropertyName1><PropertySource1>Column1 Value</PropertySource1><Timeout>100000</Timeout><AdapterWSPort>80</AdapterWSPort><uri>wss://biztalkserver:80/sites/BASSite/Shared%20Documents/Purchase%20Orders</uri></SendPort></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  When specifying TransportTypeData configuration data for an adapter that is built using the Adapter Framework, the name/value pairs that are used must all be stored into the \<AdapterConfig\> element. Since the \<AdapterConfig\> element specifies the VT_BSTR (vt="8") data type then the \< \> characters in the data must be escaped.
