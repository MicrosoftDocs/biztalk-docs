---
title: "Configuring BizTalk Adapter for Host Applications1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 553cad04-36ad-4bb8-ba9e-ad9f109e8058
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring BizTalk Adapter for Host Applications
The **BizTalk Adapter for Host Application Configuration** dialog box allows you to define and manage connections to remote IBM CICS, IMS or iSeries systems. It is launched when you click the **Connection Strings** property value field. You can use the **BizTalk Adapter for Host Application Configuration** dialog box to add a TI .NET assembly. You can use it as part of the mapping, to import, export and delete mappings, edit connection strings, and view properties of a TI .NET assembly.  

 The **Host Application Configuration** dialog box components include a toolbar, menu, data grid, and results pane. This topic contains the following sections that describe the various tasks you can perform.  

 [Toolbar and Menu Commands](../core/configuring-biztalk-adapter-for-host-applications1.md#tool)  

 [Mapping DataGrid Window](../core/configuring-biztalk-adapter-for-host-applications1.md#map)  

 [Create and Manage Mappings](../core/configuring-biztalk-adapter-for-host-applications1.md#create)  

 [Connection String Settings and Mappings](../core/configuring-biztalk-adapter-for-host-applications1.md#connStr)  

 [Upgrade from Previous Versions of Host Integration Server](../core/configuring-biztalk-adapter-for-host-applications1.md#upg)  

##  <a name="tool"></a> Toolbar and Menu Commands  
 You can access commands that create and manage connection strings through the toolbars and context-sensitive menus. You can right-click anywhere in the data grid to bring up context-sensitive menus. For example, when you right-click a connection string, you can view, edit, delete, import and export mappings. You can double-click on connection string to bring it up in edit mode. The DELETE key deletes the currently selected item, and the F1 key opens online Help.  

 The following list describes actions that you can perform:  

-   **Add a TI .NET assembly** from the global assembly cache (GAC) or by using the local file path to add an assembly to the mapping. The columns are populated with the default values reflected from the assembly. The default connection string won’t be usable if you do not enter the required values.  

-   **Delete** the selected mappings. A dialog box will appear to confirm the deletion.  

-   **Edit the connection string** part of the mapping when a mapping is selected. Launch the **Connection String** dialog box to edit the connection string.  

-   **Export mappings to XML** allows for backing up mappings. You can restore them later by using the import mapping feature. The Import/Export features allow you to share mappings among endpoints.  

-   **Import mappings or REs** allows you to import XML exported by the **BizTalk Adapter for Host Application Configuration** dialog box. You can also import RE definitions exported by TI Manager when a mapping is selected.  

-   **View Properties of TI .NET assembly** displays assembly properties. The XML tag displays the name of the input/output document this assembly supports. The Method name is part of the tag name, but it is not used when finding a mapping. All properties are read-only.  

##  <a name="map"></a> Mapping DataGrid Window  
 The **Mapping DataGrid** dialog box contains the following items:  

-   **State** (complete or incomplete). If the connection string is missing connection information, a warning indicated by a red circle with a white exclamation mark appears. After the missing information is added, the warning disappears.  

-   **ClassName** and Interface name of the TI assembly being used as part of the mapping.  

-   **Assembly** name. The strong name of the assembly if the assembly is loaded from the GAC, or the full path to the assembly if it is a local assembly. This field is auto-filled when an assembly is added, and is read-only.  

-   **Remote Environment** defines the connection string. This represents the characteristics of a remote system that receives requests from the BizTalk Host application adapter. The connection string consists of the remote environment type, programming model, remote host identification, network transport and other settings that are used when communicating with the remote host.  

-   **Remote Endpoint** DNS name or IP address of the remote IBM Host.  

-   **Result pane** displays the values for connection string of the currently selected mapping.  

##  <a name="create"></a> Create and Manage Mappings  
 This section describes tasks that you can perform.  

 **Add Assemblies to create connection string**  

 On the toolbar, click the folder icon, and then select **Add assemblies from GAC** or **Add local assembly**. **Add assemblies from GAC** will launch a dialog box that lists all the assemblies in the GAC that you can select. If you select **Add local assembly**, you can browse the locally installed assemblies.  

 Assemblies can also be added by using the **Add GAC** or **add local assembly** options from the menu.  

 **Delete a Connection string**  

 Select the mapping or mappings to delete. Click the [X] icon on the toolbar to delete the selected mappings. A dialog box is displayed so that you can confirm the deletion.  

 You can also delete mappings by using the **Delete mappings** option from the menu.  

 **Edit Connection String**  

-   The Connection string is used to hydrate the RE instance. It is populated with default values when an assembly is specified. Double-click on the selected mapping, select **Edit**, or select the **Edit connection string** menu to launch the **Connection String** dialog box. This allows you to edit the connection string for the specified RE. If the required values are not entered, an error flag will appear.  

-   The RE object validates the minimum required property values. The Connection String cell will be flagged if the required property values are not set. Required properties are listed in the [Connection String Settings and Mappings](../core/configuring-biztalk-adapter-for-host-applications1.md#connStr) section of this topic. RE validation is limited in scope, and inappropriate values could result in TI runtime errors.  

-   The dialog box displays editable and non-editable properties in a grid. The read-only textbox on the bottom displays the connection string that is created based on the values entered on the property grid. Properties are collected based on the public methods defined by the RE object, with values defined by the object itself. Some type converters and property editors are provided to facilitate editing property values.  

-   **Remote environment** displays properties that are required in order to connect to the host. Those are indicated by an asterisk (*) in the property grid. If one or more properties are missing, a red circle with a white exclamation mark is displayed on the Data grid. This warning notifies you that the missing properties can be provided by using overrides at run time.  

-   Security settings are controlled by predefined security enumerations that can be combined by using the OR operator to form new security settings.  

     The **Off** flag is exclusive to **Client**, **Package**, and **User**. **Off** will be cleared when any of the other three are checked. When **Off** is checked, all the other three options will be cleared.  

     The SSOApplication editor is ported from a previous release with minor changes. You can specify an affiliated application directly in the property grid, or use the editor to pick one created already.  

##  <a name="connStr"></a> Connection String Settings and Mappings  
 The following tables display the supported properties that define the host environment and programming model. Asterisks indicate required properties. 

 The default values are set by the RE objects themselves, and limited validation is performed.  

 **SNA User Data**  


|                        |                         |
|------------------------|-------------------------|
|      **Property**      |        **Value**        |
|      **CodePage**      |           37            |
|       **Locale**       |          1033           |
|  *\*\*LocalLUName*\*   |                         |
|    *\*\*ModeName*\*    |        PA62TKNU         |
|        **Name**        | SNAUserData. Read-only. |
|  *\*\*RemoteLUName*\*  |                         |
|      **Security**      |           Off           |
|   **SSOApplication**   |                         |
| **SynLevel2Supported** |          False          |
|      **TimeOut**       |            0            |

 *Required field.  

 **SNA Link**  


|                         |                     |
|-------------------------|---------------------|
|      **Property**       |      **Value**      |
| **AdministrationFlags** |          0          |
|      **CodePage**       |         37          |
|       **Locale**        |        1033         |
|   *\*\*LocalLUName*\*   |                     |
|    **MirrorTranId**     |        CSMI         |
|    *\*\*ModeName*\*     |      PA62TKNU       |
|        **Name**         | SNALink. Read-only. |
|  *\*\*RemoteLUName*\*   |                     |
|      **Security**       |         Off         |
|   **SSOApplication**    |                     |
| **SyncLevel2Supported** |        False        |
|       **TimeOut**       |          0          |

 *Required field.  

 **HTTP User Data**  


|                        |                          |
|------------------------|--------------------------|
|      **Property**      |        **Value**         |
| **AliasTransactionId** |                          |
|   **AllowRedirects**   |          False           |
|      **CodePage**      |            37            |
|    *\*\*HttpPort*\*    |                          |
|   *\*\*IPAddress*\*    |                          |
|       **Locale**       |           1033           |
|        **Name**        | HttpUserData. Read-only. |
|      **Security**      |           Off            |
|   **SSOApplication**   |                          |
|      **TimeOut**       |            0             |
|     **UserAgent**      |                          |
|       **UseSsl**       |          False           |

 *Required field.  

 **HTTP Link**  


|                        |                      |
|------------------------|----------------------|
|      **Property**      |      **Value**       |
| **AliasTransactionId** |                      |
|   **AllowRedirects**   |        False         |
|      **CodePage**      |          37          |
|     **Converter**      |                      |
|    *\*\*HttpPort*\*    |                      |
|   *\*\*IPAddress*\*    |                      |
|       **Locale**       |         1033         |
| **MirrorProgramName**  |                      |
|        **Name**        | HttpLink. Read-only. |
|      **Security**      |         Off          |
|   **SSOApplication**   |                      |
|      **TimeOut**       |          0           |
|    **UseConverter**    |        False         |
|     **UserAgent**      |                      |
|       **UseSsl**       |        False         |

 *Required field.  

 **IMS LU6.2**  


|                      |                     |
|----------------------|---------------------|
|     **Property**     |      **Value**      |
|     **CodePage**     |         37          |
|      **Locale**      |        1033         |
| *\*\*LocalLUName*\*  |                     |
|   *\*\*ModeName*\*   |      PA62TKNU       |
|       **Name**       | IMSLU62. Read-only. |
| *\*\*RemoteLUName*\* |                     |
|     **Security**     |         Off         |
|  **SSOApplication**  |                     |
|     **TimeOut**      |          0          |

 *Required field.  

 **IMS Connect**  


|                      |                        |
|----------------------|------------------------|
|     **Property**     |       **Value**        |
|     **CodePage**     |           37           |
| **ImsFormatModName** |                        |
|  *\*\*IPAddress*\*   |                        |
|   **ItocExitName**   |                        |
|      **Locale**      |          1033          |
|       **Name**       | IMSConnect. Read-only. |
|   **OtmaSystemId**   |                        |
|     **Security**     |          Off           |
|  **SSOApplication**  |                        |
|   *\*\*TCPPorts*\*   |                        |
|     **TimeOut**      |           0            |

 *Required field.  

 **TRM User Data/Link**  


|                                   |                         |
|-----------------------------------|-------------------------|
|           **Property**            |        **Value**        |
|           **CodePage**            |           37            |
| **ConcurrentServerTransactionId** |          MSCS           |
|         *\*\*IPAddress*\*         |                         |
|            **Locale**             |          1033           |
|             **Name**              | TRMUserData. Read-only. |
|           **Security**            |           Off           |
|        **SSOApplication**         |                         |
|         *\*\*TCPPorts*\*          |                         |
|            **TimeOut**            |            0            |

 *Required field.  

 **ELM User Data/Link**  


|                    |                         |
|--------------------|-------------------------|
|    **Property**    |        **Value**        |
|    **CodePage**    |           37            |
| *\*\*IPAddress*\*  |                         |
|     **Locale**     |          1033           |
|      **Name**      | ELMUserData. Read-only. |
|    **Security**    |           Off           |
| **SSOApplication** |                         |
|  *\*\*TCPPorts*\*  |                         |
|    **TimeOut**     |            0            |

 *Required field.  

 **Distributed Program Call**  


|                    |                                    |
|--------------------|------------------------------------|
|    **Property**    |             **Value**              |
|    **CodePage**    |                 37                 |
| *\*\*IPAddress*\*  |                                    |
|     **Locale**     |                1033                |
|      **Name**      | DistributedProgramCall. Read-only. |
|    **Security**    |                Off                 |
| **SSOApplication** |                                    |
|  *\*\*TCPPorts*\*  |                                    |
|    **TimeOut**     |                 0                  |

 *Required field.  

 **System Z Sockets User Data/Link**  


|                    |                                    |
|--------------------|------------------------------------|
|    **Property**    |             **Value**              |
|    **CodePage**    |                 37                 |
| *\*\*IPAddress*\*  |                                    |
|     **Locale**     |                1033                |
|      **Name**      | SystemzSocketsUserData. Read-only. |
|    **Security**    |                Off                 |
| **SSOApplication** |                                    |
|  *\*\*TCPPorts*\*  |                                    |
|    **TimeOut**     |                 0                  |

 *Required field.  

 **System I Sockets User Data**  


|    **Property**    |            **Value**             |
|--------------------|----------------------------------|
|    **CodePage**    |                37                |
| *\*\*IPAddress*\*  |                                  |
|     **Locale**     |               1033               |
|      **Name**      | SystemSocketUserData. Read-only. |
|    **Security**    |               Off                |
| **SSOApplication** |            \*TCPPorts            |
|    **TimeOut**     |                0                 |

 *Required field.  

 **Import Mappings**  

 To import mappings exported by BizTalk Adapter for Host Application Configuration, click on the **Import Mappings or REs** Icon. Select **Import Mappings**, or select **Import mappings** from the **File** menu. You can then browse for the XML exported by the **BizTalk Adapter for Host Application Configuration** dialog box. Select the file to import. The import process will not overwrite existing mappings.  

 **Import RE Definition**  

 Use this to import RE definitions exported by TI Manager. When a mapping is selected, click on the **Import Mappings or REs** Icon. Select **Import REs** or select **Import REs** from the **File** menu. You can then browse for the XML exported by TI Manager. A dialog box will be displayed that lists the RE definitions that you can select. Only RE definitions that have the same program model as the selected mapping will be shown.  

 **Export Mappings**  

 To export mappings to a XML file, click on the **Export mappings to XML** Icon, or select **Export mappings** from the **File** menu. You can then browse to the location where the file can be saved. You can import this file by using the **Import mapping** feature.  

 **Assembly Properties**  

 You can view relevant properties of the assembly, as well as the XML tag name of the input/output document this assembly supports. The method name is part of the tag name, but it is not used when finding a mapping. All properties are read-only. Select the mapping and then click on the assembly properties Icon, or select **show assembly properties** from the menu.  

##  <a name="upg"></a> Upgrade from Previous Versions of Host Integration Server  
 This section describes how to migrate existing BAHA applications to use Connection string:  

- If default RE was used in BAHA, export configuration using TI Manager and then import the configuration using the **Connection Strings** dialog box.  

- If non-default RE was used, associate the deployment object with the new RE in TI Manager and export the configuration in TI manager. Import the configuration using the **Connection Strings** dialog box.  

- You cannot switch REs in BizTalk Server Administration without using Connection string because the **Host Type** dialog box has been removed.  

- RE override through BizTalk Server Administration is not supported. Although you can use message context to achieve RE override, we do not recommend it. We recommend that you use connection strings.  

- If a non-default SSO application is specified, you can use TI manager to associate the RE with the non-default SSO application and continue to use static RE. Alternatively, you can specify it in the connection string.  

  **Import XML exported by TI Manager**  

  TI Manager is not required unless you are performing a migration. You can export the definition of REs and WIP objects to an XML file, which can be imported by **Connection Strings** dialog box.  

> [!WARNING]
>  TI .NET Assemblies used in mappings must have the **Include Context Parameter** property set to True or the TI method call will fail at runtime.  

 The BizTalk Adapter for Host Application Configuration makes use of the dynamic RE feature introduced in Host Integration Server 2009. With dynamic RE, the host information needed by TI runtime can be specified just before the method is invoked, as long as host connection information is known. The .NET client assembly does not have to be deployed and associated with a predefined RE in TI Manager before its methods can be invoked.  

 For BAHA, the connection information can be built into a connection string that is parsed and set to RE object created at runtime. Information about a RE can be specified when the port hosting the host application adapter is configured. It is stored as part of port configuration information managed by BizTalk administration facility. With this approach, using BAHA to integrate .NET application with host applications, you only need to use TI Designer to create the TI .NET client assemblies. All other tasks can be accomplished in BizTalk Server.  

 The following table describes the toolbar menus and actions.  

|**Tool Bar/Menu**|**Actions**|  
|------------------------|-----------------|  
|**Add Assemblies to create connection string**|Add a TI .NET assembly either from the GAC or using the local file path to add an assembly to the mapping. All the columns will be populated with the default values reflected from the assembly. The default connection string won’t be usable if some required values are not entered.|  
|**Delete a Connection string**|Deletes the selected mappings. A dialog box will be shown to confirm the deletion.|  
|**Edit the connection string**|Edit the connection string part of the mapping when a mapping is selected launch **Connection String** dialog box to edit the connection string.|  
|**Export mappings to XML**|Export allows for backing up mappings. Mappings can be imported later by using the import mapping feature. The Import/Export features provide easy share of mappings among endpoints.|  
|**Import mappings or REs**|Used to import XML exported by **BizTalk Adapter for Host Application Configuration** dialog box. Also used to import RE definitions exported by TI Manager when a mapping is selected.|  
|**View Properties of TI .NET assembly**|Displays relevant properties of the assembly, and the XML tag name of the input/output document this assembly supports. Method name is part of the tag name, but not used when finding a mapping. All properties are read-only.|  

## See Also  
 [BizTalk Adapter for Host Applications](../core/biztalk-adapter-for-host-applications2.md)