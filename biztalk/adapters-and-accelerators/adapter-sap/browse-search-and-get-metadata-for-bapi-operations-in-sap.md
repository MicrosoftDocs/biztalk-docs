---
title: "Browse, search, and get metadata for BAPI operations in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAPI operations"
  - "WCF client, generating for BAPI operations"
  - "BAPIs, browsing"
  - "searching, BAPIs"
  - "browsing, BAPIs"
  - "BAPIs, searching"
  - "BAPI operations, generating schema"
ms.assetid: 2884215a-ddba-40c7-bf9f-bfc7831f90bb
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Browse, search, and get metadata for BAPI operations in SAP
This section provides instructions on how to browse, search, and retrieve metadata from SAP for BAPI operations using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Most of the instructions are same for all three user interface. Wherever applicable, separate procedures are provided for the relevant user interface.  
  
 Before performing the steps provided in the following sections, you must have:  
  
- Created a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] project.  
  
- Connected to the SAP system using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. For instructions see [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  
  
## Browsing BAPIs in an SAP System  
 While browsing metadata using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces BAPIs as business objects and as RFCs. Browsing BAPIs as RFCs is similar to browsing an RFC in an SAP system. In such a case, the BAPIs are available as RFCs under the **RFC**. For more information on browsing RFCs, see [Browse, search, and get metadata for RFC operations in SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md).  
  
 This section provides information on browsing BAPIs as business objects. Fore more information about browsing SAP metadata, see [How Does the Adapter Surface SAP Metadata?](https://msdn.microsoft.com/library/dd788039.aspx)  
  
 Perform the following steps to browse BAPIs in an SAP system using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
 
  
#### To browse BAPIs in an SAP system  
  
1. Connect to an SAP server using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. See [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) for instructions.  
  
2. From the **Select contract type** drop-down list, select the type of contract based on whether you will be performing inbound or outbound operations using the adapter.  
  
3. In the **Select a category** box, click the BAPI node to see the BAPI functional areas in the **Available categories and operations** box. Alternatively, you can also see the BAPI functional areas by expanding the BAPI node.  
  
   > [!TIP]
   >  You can directly go to the “immediate” category node or subcategory nodes in the tree, by typing the name of the artifact in while the focus is on the tree view in the **Select a category** box. For example, to jump to the **Controlling** BAPI functional area, keep the focus on the **BAPI** node, and then type `Controlling`.  
  
    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] listing the BAPI functional areas.  
  
    ![Browsing functional areas in a BAPI](../../adapters-and-accelerators/adapter-sap/media/d4b03725-44d2-449d-a035-491cd7415139.gif "d4b03725-44d2-449d-a035-491cd7415139")  
  
4. Click the BAPI functional area to see the further categorizations of BAPI functional area.  
  
5. Click the BAPI functional area to see the relevant operations supported for that functional area. The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] with the operations supported for a particular functional area.  
  
    ![Browsing operations for a BAPI](../../adapters-and-accelerators/adapter-sap/media/1a9be42e-1f9e-4cf6-a555-c4e755fcc0ea.gif "1a9be42e-1f9e-4cf6-a555-c4e755fcc0ea")  
  
## Searching BAPIs in an SAP System  
 While searching metadata for BAPIs in an SAP system using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
- Supports wildcard characters in the search expression.  
  
- Enables search immediately under the node at which the search operation is performed.  
  
  The following table lists the special characters that can be used for search and their interpretation by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
|Special character|Interpretation|  
|-----------------------|--------------------|  
|+ (plus)|Matches exactly one character.<br /><br /> For example, A+ matches AB, AC, AD|  
|* (asterisk)|Matches zero or more characters.<br /><br /> For example, A* matches A, AB, ABC.|  
  
 For more information about the special characters supported by the adapter, see [How Does the Adapter Surface SAP Metadata?](https://msdn.microsoft.com/library/dd788039.aspx)  
  
 Perform the following steps to search BAPIs in an SAP system using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
#### To search BAPIs in an SAP system  
  
1. Connect to an SAP server using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. See [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) for instructions.  
  
2. From the **Select contract type** drop-down list, select the type of contract based on whether you will be searching for inbound or outbound operations using the adapter.  
  
3. In the **Select a category** box, click the BAPI functional area containing the BAPI you want to search.  
  
   > [!NOTE]
   >  You can search for BAPIs only at the root level.  
  
4. In the **Search in category** text box, enter a search expression to search for a specific BAPI. For example, to search for BAPIs that have "Account" in their names, type *Account\* in the text box.  
  
5. Click the button with the right-arrow icon to start the search. After the search is complete, the **Available categories and operations** box lists the BAPIs that satisfy the search criteria.  
  
6. The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] listing the BAPI search result.  
  
    ![Search BAPIs in an SAP system](../../adapters-and-accelerators/adapter-sap/media/82771a47-b656-473e-a96d-998bced38b35.gif "82771a47-b656-473e-a96d-998bced38b35")  
  
## Generating Schema for BizTalk Projects  
 You can use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate schema for selected SAP artifacts. Once you have browsed and searched for the artifacts you want to invoke, you can generate schema for those artifacts and send messages, conforming to the schema, to the SAP system.  
  
> [!NOTE]
>  You can select category nodes to return all the operations in that category's sub-tree—for example, you can select an entire BAPI sub-functional are (to generate schema for all the BAPIs in that group) or select specific BAPIs to generate schema for only those BAPIs. For more information about the nodes, see [Metadata Node IDs4](../../adapters-and-accelerators/adapter-sap/metadata-node-ids4.md).  
  
#### To retrieve metadata for BAPIs  
  
1. Connect to an SAP server using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. See [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md) for instructions.  
  
2. From the **Select contract type** drop-down list, select the type of contract based on whether you will be performing inbound or outbound operations using the adapter.  
  
3. In the **Select a category** box, click the BAPI functional group containing the BAPI for which you want to generate metadata.  
  
4. In the **Available categories and operations** box, select the functional areas or operations for which you want to generate metadata and click **Add**. The selected functional areas or operations are listed in the **Added categories and operations** box.  
  
    The following figure shows the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] listing the selected BAPIs.  
  
    ![Retrieve metadata for a BAPI](../../adapters-and-accelerators/adapter-sap/media/74170978-aef0-46c9-a6e2-36d6e9c2aefc.gif "74170978-aef0-46c9-a6e2-36d6e9c2aefc")  
  
    If you want to generate schema for multiple operations, there may be some duplicate element definitions among these schema that may cause failure in compiling the BizTalk project. For example, consider a scenario where you generate schema for an operation “Op1”. The schema for “Op1” contains a parameter of complex data type “CT1”. After generating the schema for “Op1” you close the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and re-open it to generate schema for another operation “Op2”. Assume that “Op2” also contains a parameter of complex data type “CT1”. After you exit the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] and compile the project, you will get compilation errors because the complex data type “CT1” is defined twice in different XSD files. In such situations, we recommend the following:  
  
   - Generate schema for all the operations in a single run of [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. This ensures that the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] generates only one definition for the complex data type “CT1”.  
  
   - If you want to generate schema for multiple operations across different runs of [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], make sure you select the **Generate unique schema types** check box so that the generated XSD files contain unique namespaces for the complex data type “CT1”.  
  
5. Click **OK**. The schema file is saved with an .xsd extension at the same location as the BizTalk project.  
  
   > [!NOTE]
   >  If you are using [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], by default the files are created with the naming convention "SAPBinding\<n\>.xsd", where 'n' can be 1, 2, etc. depending on the number of schema files created. Alternatively, you can provide a custom name to the schema files by entering a name in the **Filename prefix** text box. The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] now creates schema files with the naming convention \<filename prefix\>\<n\>.xsd.  
   > 
   > [!NOTE]
   >  The [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] also creates a binding file (an XML file) containing the binding properties that you specified while generating the schema for an operation and the SOAP action to invoke the operation. You can import this binding file in the BizTalk Server Administration console to create a WCF-Custom port with the connection URI, binding properties, and the SOAP action set. For more information, see [Configure a physical port binding using a port binding file to SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
6. On the **File** menu, click **Save All**.  
  
## Generating a WCF Client for BAPI Operations Using the Add Adapter Service Reference Plug-in  
 You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate WCF client code for BAPI operations (inbound operations are not supported for BAPIs).  
  
#### To generate a WCF client for BAPIs  
  
1. In the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], from the **Select contract type** drop-down list, select **Client (Outbound operations)**.  
  
2. In the **Select a category** box, expand the **BAPI** node, and then browse or search for the BAPI categories or operations for which you want to generate a WCF client.  
  
3. In the **Available categories and operations** box, select the operations or categories (BAPI functional groups) for which you want to generate a WCF client, and then click **Add**. The selected operations are listed in the **Added categories and operations** box. You can select any node that is listed in the **Available categories and operations** box. If you select a category node, then all of the operations available under that node and its sub-nodes will be selected.  
  
   > [!IMPORTANT]
   >  The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates a unique WCF client class for each business object. Depending on the categories and operations that you select, more than one WCF client class may be generated. For more information, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
4. For most scenarios the default serialization options are sufficient; however, if needed, you can control several aspects about the code that is generated and the type of serializer that is used. To set these options:  
  
   1. Click **Advanced Options** to open the **Advanced Options** box.  
  
   2. In the **Advanced Options** box under **Choose options for generated proxy**, select the options that you want. For example, you can select whether asynchronous methods are generated for the WCF client or disable the generation of a configuration file.  
  
   3. Under **Serializer** select the serializer that should be used.  
  
      The following figure shows the **Advanced Options** box with the default selections (**Auto** is selected for the serializer and no other options are selected).  
  
      ![The Advanced Options box default settings](../../adapters-and-accelerators/adapter-oracle-database/media/r2-net-adapters-oracle-msb-advanced-options.gif "R2_NET_Adapters_Oracle_MSB_Advanced_Options")  
  
      The options that you can configure in the **Advanced Options** box are equivalent to some of the options available when you use the ServiceModel Metadata Utility Tool (svcutil.exe). For more information about these options, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx). 
  
5. Click **OK**. The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] saves the WCF client class and helper code in your project directory for the selected operations and categories. By default, a configuration file is also saved. For more information, see [Generate a WCF client or a WCF service contract for SAP solution artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
## See Also  
 [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)