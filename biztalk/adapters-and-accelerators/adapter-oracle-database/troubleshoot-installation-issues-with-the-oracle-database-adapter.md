---
title: "Troubleshoot installation issues with the Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installation issues, troubleshooting"
  - "troubleshooting, installation issues"
ms.assetid: 2054b725-d657-4039-b83b-119571935f62
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot installation issues with the Oracle Database adapter
Installation of the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] copies the product binaries on the computer and registers the bindings for each adapter. This section discusses using troubleshooting techniques to resolve installation errors, and also lists some known issues.  
  
## Logging Messages for Setup Actions  
 The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup program performs the standard task of installing the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Additionally, the setup also performs certain custom actions such as registering the adapter bindings. You can log messages for both the standard as well as custom actions that the setup performs.  
  
-   The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup installs the adapter-specific files using an MSI. Therefore, the logging for the setup is the standard MSI logging. 
  
-   All logs for the custom actions that the setup program performs are available at %TEMP%\adaptersetup.log. If the tracing to the log file fails, the traces are also available in the event log.  
  
##  <a name="BKMK_OraDBBinding"></a> Setup fails to register adapter bindings  
 **Problem**  
  
 The Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard fails to register the adapter bindings, but proceeds with the adapter installation.  
  
 **Cause**  
  
 This might result due to problems with [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] installation, [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt. The adapter bindings are written to the machine.config file.  
  
 **Resolution**  
  
Manually register the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding: 
  
1.  Navigate to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  
  
     In this path, \<version\> is the version of the .NET Framework.  
  
2.  Open the file by using a text editor.  
  
3.  To register the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding:  
  
    1.  Search for the element "system.serviceModel" and add the following under it:  
  
        ```  
        <client>  
          <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
        </client>  
        ```  
  
    2.  Search for the element "bindingElementExtensions" under system.serviceModel\extensions.  
  
    3.  Look for the missing [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding. Add the following section under the "bindingElementExtensions" node.  
  
         For [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], add:  
  
        ```  
        <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    4.  Search for the element "bindingExtensions" under system.serviceModel\extensions.  
  
    5.  Look for the missing [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding. Add the following section under the "bindingExtensions" node.  
  
         For [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], add:  
  
        ```  
        <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
        ```  
  
    > [!NOTE]
    >  For information about how to determine the public key and the version, see [Determining the Public Key and Version](#BKMK_PubKey).  
  
4.  Save and close the machine.config file.  
  
####  <a name="BKMK_PubKey"></a> Determining the Public Key and Version  
 Perform the following steps to determine the public key for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
1.  Navigate to the Windows directory, typically C:\WINDOWS\assembly.  
  
2.  Right-click the DLL for which you want the public key and the version, and then select **Properties**. The following table lists the name of the DLL for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
    |Adapter|Name of the DLL|  
    |-------------|---------------------|  
    |[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]|Microsoft.Adapters.OracleDB|  
  
3.  On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL. Similarly, value against the **Version** label specifies the version number for the DLL.  
  
4.  Copy the public key, and then click **Cancel**.  
  
##  <a name="BKMK_ConsumeBinding"></a> Error while using the Consume Adapter Service add-in or Add Adapter Service Reference plug-in on a 64-bit installation  
 **Problem**  
  
 Using the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] on a 64-bit computer running 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] results in the following error:  
  
```  
No valid adapters are installed on this machine  
```  
  
 **Cause**  
  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file. A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications. So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file. However, [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] runs as a 32-bit process and hence when you launch the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], the plug-in checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.  
  
 **Resolution**  
  
-   Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  
  
    > [!IMPORTANT]
    >  You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.  
  
-   Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.  
  
    > [!NOTE]
    >  To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC. For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle's website.  
  
##  <a name="BKMK_InvalidBinding"></a> Invalid binding error while configuring Oracle database adapter ports in BizTalk Server Administration Console on a 64-bit installation  
 **Problem**  
  
 When you try to configure a port for the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you get the following error:  
  
```  
"Unable to create binding configuration element for editing. Check the values of the BindingType and BindingConfiguration properties.  
(Microsoft.Biztalk.Adapter.Wcf.Converters.CreateBindingException) Unable to get binding type for binding extension "oracleDBBinding".  
Verify the binding extension is registered in machine.config."  
```  
  
 **Cause**  
  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a WCF custom binding, which is registered under System.ServiceModel in the machine.config file. A 64-bit platform has two machine.config files, one used by the 32-bit applications and the other used by the 64-bit applications. So, when you install the 64-bit version of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)], the setup wizard registers the bindings in the 64-bit version of the machine.config file. However, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console runs as a 32-bit process and hence when you configure a port for the adapter, it checks for the bindings in the 32-bit version of the machine.config file and fails giving an error.  
  
 **Resolution**  
  
-   Install both the 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] on a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation.  
  
    > [!IMPORTANT]
    >  You must only have a 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Side-by-side installation of 32-bit and 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] on a single computer is not supported.  
  
-   Install both the 32-bit and 64-bit versions of the Oracle Data Access Components for Oracle Client 11.1.0.6 with Patch Set 11.1.0.7.  
  
    > [!NOTE]
    >  To make sure your application works with the most recent version of ODP.NET, you must have the "policy DLLs" installed on the computer and registered in the GAC. For more information, see [Oracle Data Provider for .NET](http://go.microsoft.com/fwlink/p/?LinkId=92834) on Oracle website. 
  
## See Also  
[Troubleshoot the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)