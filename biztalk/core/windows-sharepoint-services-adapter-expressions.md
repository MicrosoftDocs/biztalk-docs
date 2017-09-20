---
title: "Windows SharePoint Services Adapter Expressions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "macros, Windows SharePoint Services adapters"
  - "configuring [Windows SharePoint Services adapters], supported macros"
  - "configuring [Windows SharePoint Services adapters], expressions"
  - "Windows SharePoint Services adapters, expressions"
ms.assetid: 15e3afb2-0ef8-41b4-b3ec-de84af738c12
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows SharePoint Services Adapter Expressions
This topic describes the format and the meaning of the strings that can be specified as values for the **File NameProperty Source** properties of the Windows SharePoint Services adapter. It also describes the related context properties, **WSS.Filename** and **WSS.ConfigPropertiesXml**. These expressions allow you to easily define the file name value, or custom Windows SharePoint Service column value, based on literals as well as values extracted from the message or the BizTalk system.  
  
 The expressions can contain literals and macros. The literals will show up in the file name exactly as you type them. Macros must be placed between '%' characters. An example of a macro is `%MessageID%` which at runtime will be replaced with the GUID of the message.  
  
> [!NOTE]
>  When the % character is used as a literal or within an XPATH, it must be escaped like this \\%. A single % will be considered a macro delimiter, where a \\% will be replaced at runtime by a single %. The \ character must be escaped like this \\\\.  
  
## Expression examples  
  
|Design time value|Runtime value|  
|-----------------------|-------------------|  
|XYZ|XYZ|  
|PurchaseOrder|PurchaseOrder|  
|%MessageID%|55B93F27-7455-4066-ABE1-B4EBE6839A1A|  
|PurchaseOrder - %MessageID%|PurchaseOrder - 55B93F27-7455-4066-ABE1-B4EBE6839A1A|  
|Discount \\%10|Discount %10|  
|PurchaseOrder - %XPATH=//ns0:PurchaseOrder/ns0:ID%|PurchaseOrder – 10001|  
|PurchaseOrder - %XPATH=//ns0:PurchaseOrder/ns0:PartnerName%-%XPATH=//ns0:PurchaseOrder/ns0:ID%|PurchaseOrder – Contoso-10001|  
  
## Supported macros  
  
|Design time value|Runtime value|  
|-----------------------|-------------------|  
|%MessageID%|The BizTalk message ID which is a unique GUID.|  
|%SendingOrchestrationID%|The BizTalk ID of the orchestration instance where the message originated.|  
|%SendingOrchestrationType%|The type name of the orchestration where the message originated.|  
|%XPATH=\<xpath>%|Allows specifying an XPATH to be used for extracting the value from the message. “\<xpath>” must be replaced with a valid XPATH expression. **Note:**  The namespace alias must be defined outside the expression in the 'Namespace Aliases' or WSS.ConfigNamespaceAliases field.|  
|%Filename%|Replaced with the filename value extracted from the message context property WSS.Filename. Messages received from SharePoint have the WSS.Filename context property value set to the name of the SharePoint file. The returned value is preprocessed using Path.GetFilenameWithoutExtension. **Note:**  This macro cannot be used in WSS.Config* context properties (from orchestration).|  
|%Extension%|Replaced with the file extension value extracted from the message context property WSS.Filename. Messages received from SharePoint have the WSS.Filename context property value set to the name of the SharePoint file. The returned value is preprocessed using Path.GetExtension. The returned value will not contain ".". **Note:**  This macro cannot be used in WSS.Config* context properties (from orchestration).|  
  
 Any valid expression supported by property promotion is a valid design time file name. The design time file name will be expanded at runtime into Windows SharePoint Services file names. This Windows SharePoint Services file name has some additional limitations, which are described as follows:  
  
-   Valid Windows file names can contain any Unicode characters with the exception of the following: /  \  :  *  ?  \<  >  &#124;  "  #  {  }  %  &  ~ or tab characters and multiple periods.  
  
-   The file name cannot be longer than 256 characters and the entire URL must be less than or equal to 256 characters.  
  
-   If the expanded Windows SharePoint Services file name contains invalid characters, or if the expanded file name or URL is too long, an error will be logged in the application event log and the message will be suspended. The error and the message state will also be visible in the Group Hub page using the message event and service instance tracking.  
  
## See Also  
 [How to Configure a Windows SharePoint Services Receive Location](../core/how-to-configure-a-windows-sharepoint-services-receive-location.md)   
 [How to Configure a Windows SharePoint Services Send Handler](../core/how-to-configure-a-windows-sharepoint-services-send-handler.md)   
 [How to Configure a Windows SharePoint Services Send Port](../core/how-to-configure-a-windows-sharepoint-services-send-port.md)   
 [Windows SharePoint Services Adapter Properties Reference](../core/windows-sharepoint-services-adapter-properties-reference.md)   
 [Supported Windows SharePoint Services Column Types](../core/supported-windows-sharepoint-services-column-types.md)