---
title: "Adapter Registration File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6750f0ed-4411-4a63-a7fe-f66132cd1e22
caps.latest.revision: 35
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Registration File
After the custom adapter code has been successfully built it must be registered with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You do this by updating the registry with the appropriate adapter settings. You can manually write a registry file, but this is prone to errors due to the preciseness and complexity of the information that you need to enter. A better decision is to run the Adapter Registry Wizard. The Adapter Registry Wizard gives you all the same options as creating a registry file from scratch, and reduces the likelihood of errors in the file. For more information about the Adapter Registry Wizard, see [Adapter Registry Wizard](../core/adapter-registry-wizard.md).  
  
 The StaticAdapterManagement.reg file and DynamicAdapterManagement.reg file are located at *\<drive\>*:\Program Files\Microsoft BizTalk Server\SDK\Samples\AdaptersDevelopment\File Adapter. When you run one of these files (you can double-click it or right-click it and and select **Merge**), it registers the sample file adapter with the registry and installs the assembly into the global assembly cache. To register your custom adapter the best option is to create a new registry file by using the Adapter Registry Wizard. If your custom static adapter is similar to the sample adapter, and you decide to modify the existing registry file instead, open and modify the following properties in the StaticAdapterManagement.reg file:  
  
-   **Constraints**  
  
-   **InboundTypeName**  
  
-   **InboundAssemblyPath**  
  
-   **OutboundTypeName**  
  
-   **OutboundAssemblyPath**  
  
-   **AdapterMgmtTypeName**  
  
-   **AdapterMgmtAssemblyPath**  
  
-   **PropertyNameSpace**  
  
> [!NOTE]
>  For **OutboundAssemblyPath** and **AdapterMgmtAssemblyPath** we recommend that you not include the local path in the property value, because the configuration could break when installed on different server locations. A better choice is to use a strong name and install it in the global assembly cache.  
  
 You have two options for specifying the .NET type that implements the adapter receiver, adapter transmitter, and adapter management:  
  
1. Install the adapter to a folder and specify *TypeName and \*AssemblyPath where \*TypeName is type.FullName of the class and \*AssemblyPath is the path and file name of the assembly.  
  
2. Install the adapter in the global assembly cache and specify just *TypeName where \*TypeName is type.AssemblyQualifiedName of the class. This is the recommended option.  
  
   All adapters must have the following registry keys with the specified GUID:  
  
- **Implemented Categories\\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}**  
  
- **"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"**  
  
- **"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"**  
  
- **"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"**  
  
- **"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"**  
  
  Adapters based on the adapter framework must use these specific GUIDS for send and receive handler and location property pages. Note that if an adapter is a send-only adapter it just needs the **OutboundProtocol_PageProv**and **TransmitLocation_PageProv**GUIDs. Similarly a receive-only adapter merely requires the **InboundProtocol_PageProv** and **ReceiveLocation_PageProv** GUIDs.  
  
  The following code is from the StaticAdapterManagement.reg file, and the code for the DynamicAdapterManagement.reg file is almost identical. For more information about each of the registry properties, see [Registering an Adapter](../core/registering-an-adapter.md). After making the changes to the registry file, save the file and run it.  
  
```  
Windows Registry Editor Version 5.00  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}]  
@="Static DotNetFile Adapter"  
"AppID"="{12A6EBAA-CF68-4B58-B36E-A5A19B22C04E}"  
  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\BizTalk]  
@="BizTalk"  
"TransportType"="Static DotNetFile"  
"Constraints"=dword:00003C0b  
  
"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"  
"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"  
"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"  
"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"  
  
"InboundEngineCLSID"="{3D4B599E-2202-4bbb-9FC6-7ACA3906E5DE}"  
"InboundTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.DotNetFileReceiver""InboundAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Runtime\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Runtime.dll"  
"OutboundEngineCLSID"="{024DB758-AAF9-415e-A121-4AC245DD49EC}"  
"OutboundTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.DotNetFileTransmitter""OutboundAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Runtime\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Runtime.dll""AdapterMgmtTypeName"="Microsoft.BizTalk.SDKSamples.Adapters.Designtime.StaticAdapterManagement""AdapterMgmtAssemblyPath"="C:\\Program Files\\Microsoft BizTalk Server <version>\SDK\\Samples\\AdaptersDevelopment\\File Adapter\\Design Time\\Adapter Management\\bin\\Debug\\Microsoft.BizTalk.SDKSamples.Adapters.DotNetFile.Designtime.dll""PropertyNameSpace"="http://schemas.microsoft.com/BizTalk/2003/SDK_Samples/Messaging/Transports/dotnetfile-properties"  
"AliasesXML"="<AdapterAliasList><AdapterAlias>DotNetFILE://</AdapterAlias></AdapterAliasList>"  
"ReceiveHandlerPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"SendHandlerPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"ReceiveLocationPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
"SendLocationPropertiesXML"="<CustomProps><AdapterConfig vt=\"8\"/></CustomProps>"  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\Implemented Categories]  
[HKEY_CLASSES_ROOT\CLSID\{62018D08-281A-415b-A6D3-6172E3762867}\Implemented Categories\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}]  
```  
  
### To register the static sample adapter  
  
1. Complete the procedure to run the file adapter sample in the SDK. For more information, see [File Adapter (BizTalk Server Sample)](../core/file-adapter-biztalk-server-sample.md).  
  
2. Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Windows Explorer**.  
  
3. Navigate to the installation drive for BizTalk Server, and then navigate to **<**`drive`**>:\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**\SDK\Samples\AdaptersUsage\File Adapter**.  
  
4. To add the sample adapter to the registry, double-click **StaticAdapterManagement.reg**. (If you want to add the dynamic file adapter to the registry run **DynamicAdapterManagement.reg** instead and use that file everywhere else as appropriate.)  
  
   > [!NOTE]
   >  If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is not installed on drive C of your computer, you must modify the StaticAdapterManagement.reg file with the appropriate installation path. Search the file for C: and replace it with the correct installation drive.  
  
5. In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK** to close the dialog box, verifying that the information was added to the registry.  
  
6. To close Windows Explorer, on the **File** menu, click **Close**.  
  
    The sample static adapter is now registered with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].