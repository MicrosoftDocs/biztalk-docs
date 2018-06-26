---
title: "Troubleshoot Installation Issues with the Siebel adapter | Microsoft Docs"
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
ms.assetid: f9f066d9-37b6-4a18-9f60-d0931ea91a18
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Installation Issues with the Siebel adapter
The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation copies the product binaries on the computer and registers the bindings for each adapter. This section discusses troubleshooting techniques to resolve installation errors.  

## Setup Logging  
 The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Additionally, the setup also performs certain custom actions such as registering the adapter bindings. You can log messages for both the standard as well as custom actions performed by the setup.  

- The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter specific files using an MSI. Hence, the logging for the setup will be the standard MSI logging.  

- Logs for the custom actions performed by the setup program are available at %TEMP%\adaptersetup.log. If the tracing to the log file fails, the traces are also available in the event log.  

## Known Issues  

### Setup fails to register adapter bindings  
 **Problem**  

 The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding or the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], but proceeds with the adapter installation.  

 **Cause**  

 This might result due to problems with WCF installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config being corrupt. The adapter bindings are written to the machine.config file.  

 **Resolution**  

Manually register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding and [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] using the following steps: 

1. Navigate to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  

    In this path, \<version\> is the version of the .NET Framework.  

2. Open the file using a text editor.  

3. To register the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding:  

   1. Search for the element "system.serviceModel" and add the following under it:  

      ```  
      <client>  
        <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
      </client>  
      ```  

   2. Search for the element "bindingElementExtensions" under system.serviceModel\extensions.  

   3. Look for the missing [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding. Add the following section under the "bindingElementExtensions" node.  

       For [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], add:  

      ```  
      <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. Search for the element "bindingExtensions" under system.serviceModel\extensions.  

   5. Look for the missing [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] binding. Add the following sections under the "bindingExtensions" node.  

       For [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)], add:  

      ```  
      <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

      > [!NOTE]
      >  For information about how to determine the public key, see [Determining the Public Key and Version](#BKMK_PubKey).  

4. To register the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]:  

   1. Search for the element DbProviderFactories under the system.data node.  

   2. Look for the missing [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]. Add the following section under the DbProviderFactories node.  

       For [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], add:  

      ```  
      <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
          description=".NET Framework Data Provider for Siebel eBusiness Applications"  
          type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

5. Save and close the machine.config file.  

####  <a name="BKMK_PubKey"></a> Determining the Public Key and Version  
 Perform the following steps to determine the public key for [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] or [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)].  

###### To determine the public key  

1. Navigate to the Windows directory, typically C:\WINDOWS\assembly.  

2. Right-click the DLL for which you want the public key and select **Properties**. The following table lists the name of the DLLs for each adapter and provider.  


   |                              Adapter/ADO Provider                               |       Name of the DLL       |
   |---------------------------------------------------------------------------------|-----------------------------|
   |    [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]    |  Microsoft.Adapters.Siebel  |
   | [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] | Microsoft.Data.SiebelClient |


3. On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL. Similarly, value against the **Version** label specifies the version number for the DLL.  

4. Copy the public key, and then click **Cancel**.  

## See Also  
[Troubleshoot the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)