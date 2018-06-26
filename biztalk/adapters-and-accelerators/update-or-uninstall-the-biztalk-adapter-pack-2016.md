---
title: "Update or uninstall the BizTalk Adapter Pack 2016 | Microsoft Docs"
description: Use the setup wizard or msiexec to change or uninstall BAP 2016 included with BizTalk Server; including remove the bindings and remove the custom RFCs
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3d6c001-1005-4d7b-a143-eaa37b48f898
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Update or uninstall the BizTalk Adapter Pack 2016
How to change or uninstall the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].

<a name="BKMK_Modify_Adap"></a>
## Change or update the installation  
Before you run the setup wizard to modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, make sure the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] is installed. 
  
 You can modify the installation in interactive mode (the setup wizard), or in silent mode (the command line).
  
### Use the setup wizard  
  
1. Sign in with an account that is a member of the BizTalk Server Administrators group.  
  
2. In **Programs and features**, select **Uninstall a program**.  
  
3. Right-click **Microsoft BizTalk Adapter Pack**, and then select **Change**.  
  
4. On the Welcome screen, select **Next**.  
  
5. In **Change, repair, or remove installation**:  
  
   - To select the components you want to install, select **Change** and go to Step 6.  
  
   - To repair errors in the most recent installation, select **Repair** and go to Step 7.  
  
   - To remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from the computer, select **Remove** and then go to Step 10.  
  
6. If you chose to modify the installation:  
  
   -   Expand the **Microsoft BizTalk Adapter Pack** node to choose to install the base adapters, the .NET Framework Data Providers, or both.  
  
   -   Expand the **Base Adapters** node to choose to install all the adapters or specific adapters.  
  
   -   Expand the **ADO Providers** node to choose to install all the providers or specific providers.  
  
   -   Select **Next**.  
  
   -   Select **Change**, and then select **Finish**.  
  
7. If you chose to repair the installation, in the **Ready to repair Microsoft BizTalk Adapter Pack** dialog box, select **Repair**. The wizard starts repairing the installation.  
  
8. If required, change your preferences regarding opting for CEIP, and then select **OK**. 
  
9. Select **Finish**.  
  
10. If you chose to remove the adapters, in the **Ready to remove Microsoft BizTalk Adapter Pack** dialog box, select **Remove**, and then select **Finish**.  
  
### Use msiexec in silent mode  
  
1. Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.  
  
2. Run a command similar to the following:  
  
   > [!NOTE]
   >  To modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in a silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.  
  
   ```  
   msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
   ```  
  
    This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], and installs the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].  
  
    By using different values for the `REMOVE` and `ADDLOCAL` properties, you can add or remove specific components. Refer to the table in **Install in silent mode** at [Installing BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) for information about the values that you can use for these properties.  
  
    You can also do a silent repair by using the /f option as part of the msiexec command. For example:  
  
   ```  
   msiexec /i AdaptersSetup.msi /qn /f  
   ```  
  
    You can use various different combinations with the /f option. For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`. Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).  
  
   > [!IMPORTANT]
   >  While modifying the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP. The preferences you chose during the installation remains, even if you explicitly set the CEIP_OPTIN to true or false.  

## Uninstall or remove the BizTalk Adapter Pack  
  
> [!IMPORTANT]
>  If you created tables in the SQL Server database to work with the tRFC feature of the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], you must manually remove them before uninstalling the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation copies a `SapAdapter-DbScript-Uninstall.sql` file typically at *\<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]*. Run this file to remove the tables you created.  
  
Complete the following steps to remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from your computer. Make sure you have the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installed before you run the setup wizard.  
  
 You can remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in interactive mode (setup wizard), or in silent mode (command line).
  
### Uninstall using the setup wizard  
  
1.  In **Programs and features**, select **Uninstall a program**.  
  
2.  Right-click **Microsoft BizTalk Adapter Pack**, and then select **Uninstall**.  
  
### Uninstall in silent mode  
  
1. Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.  
  
2. Run the following command:  
  
   > [!NOTE]
   >  To remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.  
  
   ```  
   msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
   ```  
  
    This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)] from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.  
  
    By providing different values for the `REMOVE` property, you can remove specific components from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation. Refer to the table in **Install in silent mode** at [Installing BAP](../adapters-and-accelerators/installing-the-biztalk-adapter-pack-2016.md) for information about the values that you can use for this property.  
  
    To completely remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], execute the following command:  
  
   ```  
   msiexec /x AdaptersSetup.msi /qn  
   ```  
  
    For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`. Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).
  
## Remove the bindings  
 Complete these steps *only* if the setup wizard fails to remove the adapter bindings or .NET Framework Data Provider registration from the machine.config file.  
  
1. Go to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under *\<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG*.  
  
2. Open the file using a text editor.  
  
3. Remove the adapter binding registration:  
  
   1. Search for the `system.serviceModel` element, and remove the following from under the element:  
  
      ```  
      <client>  
        <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
        <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
        <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
        <endpoint binding="OracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  
  
      ```  
  
   2. Search for the `bindingElementExtensions` element under system.serviceModel\extensions.  
  
   3. Remove the following sections under the `bindingElementExtensions` node, depending on the available adapter binding. You must remove all the bindings if the setup wizard fails to remove any.  
  
       For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:  
  
      ```  
      <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:  
  
      ```  
      <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:  
  
      ```  
      <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:  
  
      ```  
      <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:  
  
      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
   4. Search for the `bindingExtensions` element under system.serviceModel\extensions.  
  
   5. Remove the following sections under the `bindingExtensions` node, depending on the available adapter binding. You must remove all the bindings if the setup wizard fails to remove any.  
  
       For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:  
  
      ```  
      <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:  
  
      ```  
      <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:  
  
      ```  
      <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:  
  
      ```  
      <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
       For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:  
  
      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  
  
4. Remove the .NET Framework Data Provider registration:  
  
   - Search for the `DbProviderFactories` element under the system.data node.  
  
   - Look for the .NET Framework Data Providers that are still registered. Remove the following sections under the `DbProviderFactories` node, depending on the existing .NET Framework Data Providers. You must remove all the providers if they exist.  
  
      For [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], remove:  
  
     ```  
     <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
         description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
     ```  
  
      For [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], remove:  
  
     ```  
     <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
         description=".NET Framework Data Provider for Siebel eBusiness Applications"  
         type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
     ```  
  
5. Save and close the machine.config file.  
  
## Remove the custom RFCs  
Complete this step to remove the custom RFCs that you installed in the SAP system. See [Install or remove custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  
  
