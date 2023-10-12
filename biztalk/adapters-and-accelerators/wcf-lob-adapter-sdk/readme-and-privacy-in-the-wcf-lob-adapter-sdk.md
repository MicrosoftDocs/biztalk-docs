---
description: "Learn more about: Readme and privacy in the WCF LOB Adapter SDK"
title: "Readme and privacy in the WCF LOB Adapter SDK"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Readme and privacy in the WCF LOB Adapter SDK
The Windows Communication Foundation (WCF) Line of Business (LOB) Adapter Software Development Kit (SDK)  
  
## Inside the SDK  
 The following table shows the content of the various components of the WCF LOB Adapter SDK in the \<Installation Folder\> after setup.  
  
|Type|Location|Description|  
|----------|--------------|-----------------|  
|Run time|\<Installation Folder\> \Bin\Microsoft.ServiceModel.Channels.dll<br /><br /> \<Installation Folder\> \Bin\Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse.dll|These assemblies contain the base run time including the main form component used within the tools.|  
|Tools|\<Installation Folder\> \Tools\Microsoft.ServiceModel.Channels.Tools.PlugInPackage.dll<br /><br /> \<Installation Folder\> \Tools\Microsoft.ServiceModel.Channels.Tools.BizTalkExtension.dll<br /><br /> \<Installation Folder\> \Tools\Microsoft.ServiceModel.Channels.Wizards.dll|**Add Adapter Service Reference Visual Studio Plug-In**<br /><br /> (.NET Project [right-click], Add Adapter Service Reference)<br /><br /> **Consume Adapter Service BizTalk Project Add-In**<br /><br /> (BizTalk Project [right-click], Add, Add Generated Items, Consume Adapter Service)<br /><br /> **WCF LOB Adapter Development Wizard**<br /><br /> (File, New, Project, Visual C#, WCF LOB Adapter)|  
|Documentation|\<Installation Folder\> \Documents\WCFLOBAdapterSDK.chm|This file contains conceptual content and the managed reference content for this release.|  
|Product Identifier File|\<Installation Folder\>\Documents\pid.txt|This file contains the product identifier of the WCF LOB Adapter SDK. Use this product identifier as a reference when contacting Microsoft Customer Service and Support (CSS).|  
|Samples|\<Installation Folder\> \Documents\Samples\ContosoAdapterSample.zip<br /><br /> \<Installation Folder\> \Documents\Samples\EchoAdapterSample.zip|The samples folder contains two sample adapters: Contoso adapter and Echo adapter.|  

## Privacy
Microsoft is committed to protecting end-users' privacy. When you build an adapter using [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], it may impact your end-users' privacy. For example, your adapter may explicitly collect and send user credentials, or it may send and receive sensitive information from a line-of-business system. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] does not send any information to Microsoft from your application unless you or the user chooses to send it to us.  
  
### Windows Communication Foundation Privacy  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is an extension to the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] and as such relies on many of the services it provides. For more information about [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] privacy, see [Windows Communication Foundation Privacy Information](/dotnet/framework/wcf/privacy-information).  
  
### Microsoft WCF LOB Adapter SDK Privacy  
 The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] is an API. As a developer, you can provide custom logging and tracing capabilities to facilitate debugging, tuning, and auditing in the adapters you create. If you do provide such capabilities, you must consider the type of information you will record and how information will be restricted so that only authorized individuals have access. This can involve the following:  
  
-   Setting and maintaining appropriate access control lists (ACLs) on log and trace files.  
  
-   Filtering sensitive data before it is written to a file.  
  
-   Encrypting sensitive data before it is written to a file.