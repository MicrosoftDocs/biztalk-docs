---
title: "Troubleshoot Installation Issues with the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "troubleshooting, installation"
  - "installation, troubleshooting"
ms.assetid: fdfdaf44-c32d-43a5-998d-02032c0b9211
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Installation Issues with the SAP adapter
Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter. This section discusses troubleshooting techniques to resolve installation errors.  

## Logging Messages for Setup Actions  
 The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Additionally, the setup also performs certain custom actions such as registering the adapter bindings. You can log messages for both the standard as well as custom actions that the setup performs.  

- The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter specific files using an MSI. Hence, the logging for the setup is the standard MSI logging.  

- Logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log. If the tracing to the log file fails, the traces are also available in the event log.  

##  <a name="BKMK_SAPSetupBinding"></a> Setup fails to register adapter bindings or data providers  
 **Problem**  

 The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings or the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)], but proceeds with the adapter installation.  

 **Cause**  

 This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt. The adapter bindings are written to the machine.config file.  

 **Resolution**  

 You should manually register the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding or the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  

### Register the adapter bindings or the data provider  

1. Navigate to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  

    In this path, \<version\> is the version of the .NET Framework.  

2. Open the file using a text editor.  

3. To register the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding:  

   1. Search for the element "system.serviceModel" and add the following under it:  

      ```  
      <client>  
        <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
      </client>  
      ```  

   2. Search for the element "bindingElementExtensions" under system.serviceModel\extensions.  

   3. Look for the missing [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding. Add the following section under the "bindingElementExtensions" node.  

       For [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], add:  

      ```  
      <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. Search for the element "bindingExtensions" under system.serviceModel\extensions.  

   5. Look for the missing [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding. Add the following section under the "bindingExtensions" node.  

       For [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], add:  

      ```  
      <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

      > [!NOTE]
      >  For information about how to determine the public key, see [Determining the Public Key and Version](#BKMK_PubKey).  

4. To register the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]:  

   1. Search for the element "DbProviderFactories" under the "system.data" node.  

   2. Look for the missing [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]. Add the following section under the "DbProviderFactories" node.  

       For [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], add:  

      ```  
      <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient" description=".NET Framework Data Provider for mySAP Business Suite" type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

5. Save and close the machine.config file.  

###  <a name="BKMK_PubKey"></a> Determining the Public Key and Version  
 Perform the following steps to determine the public key for [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] or [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  

1. Navigate to the Windows directory, typically C:\WINDOWS\assembly.  

2. Right-click the DLL for which you want the public key, and then select **Properties**. The following table lists the name of the DLLs for [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] and [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  


   |                           Adapter/Data Provider                           |     Name of the DLL      |
   |---------------------------------------------------------------------------|--------------------------|
   |    [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]    |  Microsoft.Adapters.SAP  |
   | [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] | Microsoft.Data.SAPClient |


3. On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL. Similarly, value against the **Version** label specifies the version number for the DLL.  

4. Copy the public key, and then click **Cancel**.  

##  <a name="BKMK_SAPConsumeBinding"></a> No valid adapters are installed error

 **Problem**  

 Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:  

```  
No valid adapters are installed on this machine  
```  

 **Cause**  

 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file. A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications. So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file. However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.  

 **Resolution**  

- Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  

  > [!IMPORTANT]
  >  You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.  

- Add both the 32-bit and 64-bit versions of the client DLLs for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (such as librfc32u.dll) to the PATH variable. The 32-bit version of the DLLs must be added to C:\Windows\SysWow64 folder. The 64-bit version of the DLLs must be added to C:\Windows\System32 folder.  

  > [!IMPORTANT]
  >  If the adapter (32 or 64-bit) is running on a computer that has a 64-bit operating system, and you are using the adapter to write an application, you should mark the application to the same type (32 or 64-bit) as the adapter. Also, the version of the RFC SDK (32 or 64-bit) must be same as the version of the adapter (32 or 64-bit).  
  >   
  >  For example, if a 32-bit adapter is running on a computer with a 64-bit operating system, the adapter client application must be marked as 32-bit.  

   For more information about the SAP client DLLs, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  

##  <a name="BKMK_SAPInvalidBinding"></a> Invalid binding error while configuring SAP adapter ports  
 **Problem**  

 When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:  

```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sapBinding".  
Verify the binding extension is registered in machine.config."  
```  

 **Cause**  

 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file. A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications. So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file. However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.  

 **Resolution**  

- Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  

  > [!IMPORTANT]
  >  You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.  

- Add both the 32-bit and 64-bit versions of the client DLLs for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] (such as librfc32u.dll) to the PATH variable. The 32-bit version of the DLLs must be added to C:\Windows\SysWow64 folder. The 64-bit version of the DLLs must be added to C:\Windows\System32 folder.  

  > [!IMPORTANT]
  >  If the adapter (32 or 64-bit) is running on a computer that has a 64-bit operating system, and you are using the adapter to write an application, you should mark the application to the same type (32 or 64-bit) as the adapter. Also, the version of the RFC SDK (32 or 64-bit) must be same as the version of the adapter (32 or 64-bit).  
  >   
  >  For example, if a 32-bit adapter is running on a computer with a 64-bit operating system, the adapter client application must be marked as 32-bit.  

   For more information about the SAP client DLLs, see [Install Custom RFCs for the Data Provider for SAP](../../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).

## See Also  
[Troubleshoot the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)