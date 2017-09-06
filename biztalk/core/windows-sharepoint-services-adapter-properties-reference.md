---
title: "Windows SharePoint Services Adapter Properties Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ConfigCustomTemplatesDocLib property [Windows SharePoint Services adapters]"
  - "InFileSize property [Windows SharePoint Services adapters]"
  - "InIconUrl property [Windows SharePoint Services adapters]"
  - "InOfficeIntegration property [Windows SharePoint Services adapters]"
  - "code samples, Windows SharePoint Services adapters"
  - "Windows SharePoint Services adapters, properties"
  - "ConfigCustomTemplatesNamespaceCol property [Windows SharePoint Services adapters]"
  - "configuring [Windows SharePoint Services adapters], properties"
  - "ConfigTemplatesDocLib property [Windows SharePoint Services adapters]"
  - "InPropertiesXml property [Windows SharePoint Services adapters]"
  - "InItemId property [Windows SharePoint Services adapters]"
  - "InListName property [Windows SharePoint Services adapters]"
  - "InArchivedMsgUrl property [Windows SharePoint Services adapters]"
  - "Filename property [Windows SharePoint Services adapters]"
  - "InListUrl property [Windows SharePoint Services adapters]"
  - "ConfigTemplatesNamespaceCol property [Windows SharePoint Services adapters]"
  - "InLastModifiedBy property [Windows SharePoint Services adapters]"
  - "ConfigOverwrite property [Windows SharePoint Services adapters]"
  - "ConfigPropertiesXml property [Windows SharePoint Services adapters]"
  - "TransmittedFileLocation property [Windows SharePoint Services adapters]"
  - "InTitle property [Windows SharePoint Services adapters]"
  - "Windows SharePoint Services adapters, code samples"
  - "InCreated property [Windows SharePoint Services adapters]"
  - "InCreatedBy property [Windows SharePoint Services adapters]"
  - "InLastModified property [Windows SharePoint Services adapters]"
  - "URL property [Windows SharePoint Services adapters]"
  - "InEditUrl property [Windows SharePoint Services adapters]"
  - "ConfigOfficeIntegration property [Windows SharePoint Services adapters]"
  - "ConfigTimeout property [Windows SharePoint Services adapters]"
  - "ConfigNamespaceAliases property [Windows SharePoint Services adapters]"
  - "ConfigAdapterWSPort property [Windows SharePoint Services adapters]"
ms.assetid: c64c43ac-05bb-427c-987a-71663ae8e43d
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows SharePoint Services Adapter Properties Reference
The following Windows SharePoint Services adapter properties are promoted into BizTalk Server or are used to specify send port configuration options for outgoing messages. The properties can be used to access Windows SharePoint Services information regarding the message or to provide information to the Windows SharePoint Services adapter from within an orchestration.  
  
## Message property precedence  
 There is a rule of precedence for overriding the message properties defined in orchestrations and send ports.  
  
 The following are the rules:  
  
1.  Property defined in the orchestration inside of PropertiesXML  
  
2.  Property defined in the orchestration  
  
3.  Property defined at the send port level inside of the Property Name/ or Property Source collection  
  
4.  Property defined at the send port level  
  
## Considerations and Known Issues  
 The following are considerations for the Windows SharePoint Services adapter properties:  
  
-   The list of properties in orchestrations is merged with the properties defined by the port based on property position. If there are conflicts, the orchestration property will override the send port property.  
  
## Property types  
  
|Property Type|Description|  
|-------------------|-----------------|  
|**IN**|IN properties are BizTalk Server properties that get their value from Windows SharePoint Services. **Note:**  You should not modify these properties from within orchestrations.|  
|**CONFIG**|CONFIG properties are properties that get their value from BizTalk orchestrations or custom pipelines. This value is used by the Windows SharePoint Services adapter when determining the destination of the outgoing messages. CONFIG properties allow you to specify the value of some of the properties within an orchestration or custom pipeline that you would otherwise have to define on the send port. Properties that don’t begin with IN or CONFIG are both IN and CONFIG, except for the URL property.|  
|**PROMOTED**|PROMOTED properties can be used by content-based routing (CBR). Properties that are not marked as PROMOTED cannot be used by CBR. **Note:**  Although all adapter properties show up in the CBR filter editor, only the promoted properties can be used for CBR.|  
|**SPECIAL**|N/A|  
  
> [!NOTE]
>  All properties exist under the http://schemas.microsoft.com/BizTalk/2006/WindowsSharePointServices-properties namespace and are accessible from an orchestration or send port filter using the `WSS.<WSS_Property_Name>` syntax.  
  
## Property list  
  
|Windows SharePoint Services Standard Column|Windows SharePoint Services Property Name and Type|Type|Description|Property Type|  
|-------------------------------------------------|--------------------------------------------------------|----------|-----------------|-------------------|  
|Name|Filename|xs:string|The file name with the extension of the Windows SharePoint Services file. File names, including extensions, are unique within a document library.|IN/CONFIG/ PROMOTED|  
|N/A|Url|xs:string|The URL of the file.|IN/PROMOTED|  
|N/A|TransmittedFileLocation|N/A|This property is used by Business Activity Monitoring (BAM) for integration purposes and is not available in orchestrations.|SPECIAL|  
|N/A|InArchivedMsgUrl|xs:string|The URL of the file in the archive document library. This property is not available if the receive location is not archiving the message.|IN/PROMOTED|  
|Type|InIconUrl|xs:string|The URL of the Windows SharePoint Services icon that is used to represent the document.|IN|  
|Title|InTitle|xs:string|The title of the Windows SharePoint Service file. This is different from the file name. Titles don’t have to be unique within a document library.|IN/PROMOTED|  
|Modified|InLastModified|xs:dateTime|The last modified date of the Windows SharePoint Service.|IN/PROMOTED|  
|Modified By|InLastModifiedBy|xs:string|The name of the last user that modified the file.|IN/PROMOTED|  
|ID|InItemId|xs:int|The ID of the file. This is an integer unique within the document library which can be used to access the file.|IN|  
|Edit|InEditUrl|xs:string|The URL that can be accessed to edit the properties of the file.|IN|  
|Created|InCreated|xs:dateTime|The date when the Windows SharePoint Service file was created.|IN/PROMOTED|  
|Created By|InCreatedBy|xs:string|The user that created the file.|IN/PROMOTED|  
|File Size|InFileSize|xs:int|The size of the Windows SharePoint Services file.|IN|  
|N/A|InListName|xs:string|The name of the document library where this file is located.|IN/PROMOTED|  
|N/A|InListUrl|xs:string|The URL of the document library, or document library folder where this file is located.|IN|  
|N/A|InPropertiesXml|xs:string|A flat XML document that contains all the standard and user defined Windows SharePoint Services columns. It allows access to any Windows SharePoint Services column value from an orchestration, including the values of the user-defined columns. **Note:**  It does not have the 16-column limitation. **Note:**  See the sample InPropertiesXml value in the next section of this topic.|IN|  
|N/A|InOfficeIntegration|xs:string|Based on the value of the receive location. This is either `yes`, `no`, or `optional`.|IN|  
|N/A|ConfigOverwrite|xs:string|"Yes" overwrites the already existing files with the same name. "No" raises an error when a file with the same name exists. "Rename" changes the file to a unique name by appending a unique sequence to the file name. **Note:**  This is similar to the 'Overwrite' field for physical send ports. **Note:**  'Orchestration' is not a valid value for this field.|CONFIG|  
|N/A|ConfigNamespaceAliases|xs:string|The alias definitions of the XPATHs.|CONFIG|  
|N/A|ConfigOfficeIntegration|xs:string|'Yes' if the OfficeImporters should be called. 'No' to handle the message as-is. 'Optional' results in 'Yes' if IP solution is found, otherwise 'No'. **Note:**  This is similar to the 'Microsoft Office Integration' field for physical send ports. **Note:**  'Orchestration' is not a valid value for this field.|CONFIG|  
|N/A|ConfigTemplatesDocLib|xs:string|Fallback document library name. This is the second place that is searched. **Note:**  This is similar to the Templates Fallback Document Library field for physical send ports.|CONFIG|  
|N/A|ConfigTemplatesNamespaceCol|xs:string|Namespace column name for fallback document library. **Note:**  This is similar to the 'Templates Fallback Namespace Column' field for physical send ports.|CONFIG|  
|N/A|ConfigCustomTemplatesDocLib|xs:string|Primary document library name. This is the first place searched. **Note:**  This is similar to the Templates Document Library field for physical send ports.|CONFIG|  
|N/A|ConfigCustomTemplatesNamespaceCol|xs:string|Namespace column name for primary document library. **Note:**  This is similar to the Templates Namespace Column field for physical send ports.|CONFIG|  
|N/A|ConfigPropertiesXml|xs:string|A flat XML document that contains all the Windows SharePoint Services column names and values that follow to be updated in Windows SharePoint Services. It allows an orchestration developer to set the SharePoint column values for the subsequent message to be created in SharePoint. **Note:**  This is similar to the functionality available through the Column n and Column n Value fields for physical send ports. **Note:**  It has a 16 column limitation. **Note:**  See the sample ConfigPropertiesXml value later in this topic.|CONFIG|  
|N/A|ConfigTimeout|xs:int|Time-out in milliseconds for Web service calls.|CONFIG|  
|N/A|ConfigAdapterWSPort|xs:int|The port or IIS Web site where the adapter has been installed and configured. **Note:**  An invalid port configuration value in an orchestration will suspend the message even if the physical send port value overrides the orchestration defined value.|CONFIG|  
  
## Sample InPropertiesXml  
 The following is sample XML for InPropertiesXml.  
  
```  
<InPropertiesXml>  
     <Property name="InItemId">2</Property>  
     <Property name="Created">12/14/2004 1:30:31 PM</Property>  
     <Property name="Author">3;#John Doe</Property>  
     <Property name="Modified">12/14/2004 1:30:31 PM</Property>  
     <Property name="Editor">3;#John Doe</Property>  
     <Property name="_ModerationStatus">0</Property>  
     <Property name="_ModerationComments" />  
     <Property name="FileRef">/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="FileDirRef">2;#sites/BASSite/SourceLibrary</Property>  
     <Property name="InLastModified">2004-12-14 13:30:31</Property>  
     <Property name="InCreated">2004-12-14 13:30:31</Property>  
     <Property name="InFileSize">7338</Property>  
     <Property name="FSObjType">0</Property>  
     <Property name="CheckedOutUserId">2;#3</Property>  
     <Property name="Filename">PO1.xml</Property>  
     <Property name="VirusStatus">2;#7338</Property>  
     <Property name="CheckedOutTitle">2;#John Doe</Property>  
     <Property name="LinkCheckedOutTitle">John Doe</Property>  
     <Property name="InLastModifiedBy">MyDomain\jdoe</Property>  
     <Property name="InCreatedBy">MyDomain\jdoe</Property>  
     <Property name="owshiddenversion">1</Property>  
     <Property name="File_x0020_Type">xml</Property>  
     <Property name="HTML_x0020_File_x0020_Type" />  
     <Property name="_SourceUrl" />  
     <Property name="_SharedFileIndex" />  
     <Property name="LinkFilenameNoMenu">PO1.xml</Property>  
     <Property name="LinkFilename">PO1.xml</Property>  
     <Property name="SelectTitle">2</Property>  
     <Property name="SelectFilename">2</Property>  
     <Property name="Edit">xml</Property>  
     <Property name="InIconUrl">/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="Url">http://localhost:80/sites/BASSite/SourceLibrary/PO1.xml</Property>  
     <Property name="EncodedAbsUrl">PO1</Property>  
     <Property name="BaseName">7338</Property>  
     <Property name="FileSizeDisplay" />  
     <Property name="InstanceID">200</Property>  
     <Property name="Order" />  
     <Property name="InTitle" />  
     <Property name="ColumnOne" />  
     <Property name="ColumnTwo" />  
     <Property name="ColumnThree" />  
     <Property name="ColumnFour" />  
     <Property name="InListName">SourceLibrary</Property>  
     <Property name="InListUrl">http://localhost:80/sites/BASSite/SourceLibrary</Property>  
     <Property name="InEditUrl">http://localhost:80/sites/BASSite/SourceLibrary/Forms/EditForm.aspx?ID=2</Property>  
     <Property name="InOfficeIntegration">yes</Property>  
</InPropertiesXml>  
```  
  
## Sample ConfigPropertiesXml  
 The following is sample XML for ConfigPropertiesXml.  
  
```  
<ConfigPropertiesXml>  
     <PropertyName1>PO number</PropertyName1>  
     <PropertySource1>%XPATH=//orchns:PurchaseOrder/orchns:Header/orchns:ID%</PropertySource1>  
     <PropertyName2>Charge To</PropertyName2>  
     <PropertySource2>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:chargeTo%</PropertySource2>  
     <PropertyName3>PO Priority</PropertyName3>  
     <PropertySource3>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:priority%</PropertySource3>  
     <PropertyName4>Order Date</PropertyName4>  
     <PropertySource4>%XPATH=//orchns:PurchaseOrder/orchns:orderBody/orchns:dateOrdered%</PropertySource4>  
</ConfigPropertiesXml>  
```  
  
## See Also  
 [How to Configure a Windows SharePoint Services Receive Location](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [How to Configure a Windows SharePoint Services Send Handler](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [How to Configure a Windows SharePoint Services Send Port](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [How to Create a Send Port](../core/how-to-create-a-send-port2.md)   
 [Windows SharePoint Services Adapter Expressions](../core/windows-sharepoint-services-adapter-expressions.md)   
 [Supported Windows SharePoint Services Column Types](../core/supported-windows-sharepoint-services-column-types.md)