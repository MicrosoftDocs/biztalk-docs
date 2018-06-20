---
title: "Troubleshoot Installation Issues with the SQl adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48778158-6064-4731-be72-1af855ebe373
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Installation Issues with the SQl adapter
> [!IMPORTANT]
>  The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is available as part of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] as well as a separate adapter. If you are accessing this topic to know about installation issues with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] that is separate from the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], all references to the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Setup must be interpreted as [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] Setup.  

 Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter. This section discusses using troubleshooting techniques to resolve installation errors.  

## Logging Messages for Setup Actions  
 The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Additionally, the setup also performs certain custom actions such as registering the adapter bindings. You can log messages for both the standard as well as custom actions that the setup performs.  

- The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI. Therefore, the logging for the setup is the standard MSI logging.  

- All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log. If the tracing to the log file fails, the traces are also available in the event log.  

## Known Issues  
 The following are the most common errors you might encounter when installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], along with their probable cause and resolution.  



###  <a name="BKMK_SQLSetupBinding"></a> Setup fails to register adapter bindings  
 **Problem**  

 The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] Setup Wizard fails to register the adapter bindings, but proceeds with the adapter installation.  

 **Cause**  

 This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt. The adapter bindings are written to the machine.config file.  

 **Resolution**  

 You should manually register the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding.  

##### To register the adapter binding  

1. Navigate to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  

    In this path, \<version\> is the version of the .NET Framework.  

2. Open the file by using a text editor.  

3. To register the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding:  

   1. Search for the element "system.serviceModel" and add the following under it:  

      ```  
      <client>  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  
      ```  

   2. Search for the element "bindingElementExtensions" under system.serviceModel\extensions.  

   3. Look for the missing [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding. Add the following section under the "bindingElementExtensions" node.  

       For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. Search for the element "bindingExtensions" under system.serviceModel\extensions.  

   5. Look for the missing [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding. Add the following section under the "bindingExtensions" node.  

       For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   > [!NOTE]
   >  For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).  

4. Save and close the machine.config file.  

####  <a name="BKMK_PubKey"></a> Determining the Public Key and Version  
 Perform the following steps to determine the public key for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

###### To determine the public key  

1. Navigate to the Windows directory, typically C:\WINDOWS\assembly.  

2. Right-click the DLL for which you want the public key and the version, and then select **Properties**. The following table lists the name of the DLL for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  


   |                              Adapter                              |    Name of the DLL     |
   |-------------------------------------------------------------------|------------------------|
   | [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] | Microsoft.Adapters.Sql |


3. On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL. Similarly, value against the **Version** label specifies the version number for the DLL.  

4. Copy the public key, and then click **Cancel**.  

###  <a name="BKMK_SQLConsumeBinding"></a> Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation  
 **Problem**  

 Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:  

```  
No valid adapters are installed on this machine  
```  

 **Cause**  

 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file. A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications. So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file. However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.  

 **Resolution**  

 Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  

> [!IMPORTANT]
>  You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.  

###  <a name="BKMK_SQLInvalidBinding"></a> Invalid binding error while configuring SQL adapter ports in BizTalk Server Administration Console on a 64-bit installation  
 **Problem**  

 When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:  

```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "sqlBinding".  
Verify the binding extension is registered in machine.config."  
```  

 **Cause**  

 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file. A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications. So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file. However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.  

 **Resolution**  

 Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  

> [!IMPORTANT]
>  You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.  

## See Also  
 [Troubleshoot the SQL adapter](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)