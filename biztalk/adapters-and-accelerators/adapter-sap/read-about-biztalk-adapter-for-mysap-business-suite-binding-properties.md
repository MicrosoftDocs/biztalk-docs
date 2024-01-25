---
description: "Learn more about: Read about BizTalk Adapter for mySAP Business Suite binding properties"
title: "Read about BizTalk Adapter for mySAP Business Suite binding properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Read about BizTalk Adapter for mySAP Business Suite binding properties
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces several binding properties that enable you to control some of its run-time and design-time behavior. This section describes these binding properties and provides links to topics that explain how you can set them.  

## The SAP Adapter Binding Properties  
 The following table shows the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding properties grouped by category. The category refers to the node under which each binding property appears in the dialog boxes that are presented by different applications to configure the adapter (SAPBinding).  

- **CloseTimeout** binding property: Specifies the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] connection close timeout. The default is 1 minute.

  - **Category**: General
  - **.NET Type**: System.DateTime 

- **DataTypesBehavior** binding property: The SAP system does not enforce correct values to be specified for DATS, TIMS, and NUMC fields. So, if invalid values are present in the SAP data store for DATS, TIMS, and NUMC fields and a client program tries to read the values using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the adapter throws an exception.

  - **Category**: General
  - **.NET Type**: Microsoft.Adapters.SAP.SapDataTypesBehavior

  The SAP system has special values for representing minimum and maximum values for the DATS, TIMS, and NUMC fields for which there is no equivalent .NET type. For example, the minimum and maximum values for a DATS field are 00000000 and 99999999 respectively, for which there is no equivalent .NET type DateTime. Moreover, converting the minimum and maximum values for DATS fields to DateTime.MinValue and DateTime.Max value is not feasible because the minimum or maximum value for DATS field and minimum or maximum value for a .NET DateTime type are not the same.

  To enable adapter clients to control the adapter behavior when special values are encountered in the SAP system, you can set the **DataTypesBehavior** binding property. This is a complex binding property that has the following sub-properties:
  
  - **DateTimeMaxToDats**: Specifies the behavior the adapter should follow to send a DATS value when the adapter client sends the value DateTime.MAX, which is “9999-12-31T23:59:59.9999999”. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if the client program sends the DateTime.MAX value.
    - **\<VALUE\>**: When set to this, the adapter sends the specified value to SAP if the client program sends the DateTime.MAX value. Default is 99991231.

  - **DateTimeMaxToTims**: Specifies the behavior the adapter should follow to send a TIMS value when the adapter client sends the value DateTime.MAX, which is “9999-12-31T23:59:59.9999999”. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if the client program sends the DateTime.MAX value.
    - **\<VALUE\>**: When set to this, the adapter sends the specified value to SAP if the client program sends the DateTime.MAX value. Default is 235959.

  - **DateTimeMinToDats**: Specifies the behavior the adapter should follow to send a DATS value when the adapter client sends the value DateTime.MIN, which is “0001-01-01T00:00:00”. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if the client program sends the DateTime.MIN value.
    - **\<VALUE\>**: When set to this, the adapter sends the specified value to SAP if the client program sends the DateTime.MIN value. Default is 00010101.

  - **DateTimeMinToTims:**  Specifies the behavior the adapter should follow to send a TIMS value when the adapter client sends the value DateTime.MIN, which is “0001-01-01T00:00:00”. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if the client program sends the DateTime.MIN value.
    - **\<VALUE\>**: When set to this, the adapter sends the specified value to SAP if the client program sends the DateTime.MIN value. Default is 000000.

  - **DateTimeNullToDats:**  Specifies the behavior the adapter should follow to send a DATS value when the adapter client sends a NULL DateTime value. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if the client program sends a NULL DateTime value.
    - **SKIP** (default): When set to this, the adapter skips the field and does not send any value to SAP if the client program sends a NULL DateTime value.
    - **\<VALUE\>**: When set to this, the adapter sends the specified value to SAP if the client program sends a NULL DateTime value.

  - **DateTimeNullToTims:**  Specifies the behavior the adapter should follow to send a TIMS value when the adapter client sends a NULL DateTime value. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if the client program sends a NULL DateTime value.
    - **SKIP** (default): When set to this, the adapter skips the field and does not send any value to SAP if the client program sends a NULL DateTime value.
    - **\<VALUE\>**: When set to this, the adapter sends the specified value to SAP if the client program sends a NULL DateTime value.

  - **DatsMaxToDateTime:**  Specifies the behavior the adapter should follow to retrieve a DateTime value when the adapter receives a DATS.MAX value, which is 99999999, from SAP. You could set this to the following values:

    - **ERROR** (default): When set to this, the adapter throws an error if it receives a DATS.MAX value from SAP.
    - **NULL**: When set to this, the adapter returns NULL if it receives a DATS.MAX value from SAP.
    - **\<VALUE\>**: When set to this, the adapter parses the specified value in the XSD:DateTime format and returns it to the client program.

  - **DatsMinToDateTime:**  Specifies the behavior the adapter should follow to retrieve a DateTime value when the adapter receives a DATS.MIN value, which is 00000000, from SAP. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if it receives a DATS.MIN value from SAP.
    - **NULL**: When set to this, the adapter returns NULL if it receives a DATS.MIN value from SAP.
    - **\<VALUE\>**: When set to this, the adapter parses the specified value in the XSD:DateTime format and returns it to the client program.

    Default is:

      - BizTalk Server 2020 CU1 and earlier: ERROR.
      - BizTalk Server 2020 CU2 and newer: 0001-01-01T00:00:00.

  - **EmptyDatsToDateTime:**  Specifies the behavior the adapter should follow to retrieve a DateTime value when the adapter receives an empty DATS value from SAP. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if it receives an empty DATS value from SAP.
    - **NULL**: When set to this, the adapter returns NULL if it receives an empty DATS value from SAP.
    - **\<VALUE\>**. When set to this, the adapter parses the specified value in the XSD:DateTime format and returns it to the client program. Default is 0001-01-01T00:00:00.

  - **EmptyNumcToInt:**  Specifies the behavior the adapter should follow to retrieve an integer value when the adapter receives an empty NUMC value (all spaces) from SAP. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if it receives an empty NUMC value from SAP.
    - **NULL**: When set to this, the adapter returns NULL if it receives an empty NUMC value from SAP.
    - **\<VALUE\>**. When set to this, the adapter assumes that the specified value is a valid Int32 or Int64 value and returns it to the client program. Default is 0.

  - **EmptyTimsToDateTime:**  Specifies the behavior the adapter should follow to retrieve a DateTime value when the adapter receives an empty TIMS value from SAP. You could set this to the following values:

    - **ERROR**: When set to this, the adapter throws an error if it receives an empty TIMS value from SAP.
    - **NULL**: When set to this, the adapter returns NULL if it receives an empty TIMS value from SAP.
    - **\<VALUE\>**. When set to this, the adapter parses the specified value in the XSD:DateTime format and returns it to the client program. Default is 0001-01-01T00:00:00.

  - **InvalidDatsToDateTime:**  Specifies the behavior the adapter should follow to retrieve a DateTime value when the adapter receives an invalid DATS value from SAP. You could set this to the following values:
    - **ERROR** (default): When set to this, the adapter throws an error if it receives an invalid DATS value from SAP.
    - **NULL**: When set to this, the adapter returns NULL if it receives an invalid DATS value from SAP.
    - **\<VALUE\>**. When set to this, the adapter parses the specified value in the XSD:DateTime format and returns it to the client program.

  - **InvalidNumcToInt:**  Specifies the behavior the adapter should follow to retrieve an integer value when the adapter receives an invalid NUMC value from SAP. You could set this to the following values:
    - **ERROR**: When set to this, the adapter throws an error if it receives an invalid NUMC value from SAP.
    - **NULL**: When set to this, the adapter returns NULL if it receives an invalid NUMC value from SAP.
    - **\<VALUE\>**. When set to this, the adapter assumes that the specified value is a valid Int32 or Int64 value and returns it to the client program. Default is 0.

  - **TimsMaxToDateTime:**  Specifies the behavior the adapter should follow to retrieve a DateTime value when the adapter receives a TIMS.MAX value from SAP. You could set this to the following values:
    - **ERROR** (default): When set to this, the adapter throws an error if it receives a TIMS.MAX value from SAP.
    - **NULL**: When set to this, the adapter returns NULL if it receives a TIMS.MAX value from SAP.
    - **\<VALUE\>**. When set to this, the adapter parses the specified value in the XSD:DateTime format and returns it to the client program.

- **Name** binding property: Not supported.

  - **Category**: General
  - **.NET Type**: string

- **OpenTimeout** binding property: Specifies the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] connection open timeout. The default is 1 minute.

  - **Category**: General
  - **.NET Type**: System.DateTime

- **ReceiveTimeout** binding property: Specifies the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] message receive timeout. Essentially, this means the maximum amount of time the adapter waits for an inbound message. The default is 10 minutes.

  - **Category**: General
  - **.NET Type**: System.DateTime

  For inbound operations such as receiving IDOCs, we recommend setting the timeout to the maximum possible value; which is 24.20:31:23.6470000 (24 days). When using the adapter with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], setting the timeout to a large value does not impact the functionality of the adapter.

- **SendTimeout** binding property: Specifies the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] message send timeout. The default is 1 minute.

  - **Category**: General
  - **.NET Type**: System.DateTime

- **EnableBizTalkCompatiblityMode** binding property: Specifies whether the BizTalk Layered Channel Binding Element should be loaded. The BizTalk Layered Channel Binding Element is loaded to enable BizTalk transactions to flow through the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the SAP system.

  - **Category**: BizTalk
  - **.NET Type**: bool (System.Boolean)

  What you need to know:
  
  - Set this to **true** to load the binding element. Otherwise, set this to **false**.
  - When using the adapters from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always set the property to **true**. When using the adapters from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must always set the property to **false**.

- **EnableBusinessObjects** binding property: This property is deprecated. The adapter always displays the **BAPI** node when browsing the metadata using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. The behavior is the same as setting **EnableBusinessObjects** to **true** in [!INCLUDE[adapterpackversion](../../includes/adapterpackversion-md.md)] 1.0.

  - **Category**: Bapi
  - **.NET Type**: bool (System.Boolean)

- **EnableConnectionPooling** binding property: Specifies whether the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] connection pool is enabled. The default is **true**, which specifies that the connection pool is enabled.

  - **Category**: Connection
  - **.NET Type**: bool (System.Boolean)

- **IdleConnectionTimeout** binding property: Specifies the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] idle connection timeout. When a connection in the pool is idle (unused) for a period that exceeds this timeout, the connection will be disposed. The default is 15 minutes. The idle connection timeout only applies to connections in the pool that are not being used. It does not affect active (open) connections which may be waiting for data.

  - **Category**: Connection
  - **.NET Type**: System.DateTime

- **MaxConnectionsPerSystem** binding property: Specifies the maximum number of connections in the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] connection pool. The default is 50. **MaxConnectionsPerSystem** is a static property within an application domain. This means that when you change **MaxConnectionsPerSystem** for one binding instance in an application domain, the new value applies to all objects created from all binding instances within that application domain.

  - **Category**: Connection
  - **.NET Type**: int (System.Int32)

  By default, the SAP client library (librfc32u.dll) supports a maximum of 100 connections to the SAP system. If you exceed this number of connections, an exception will be thrown by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. For this reason, you should not set **MaxConnectionsPerSystem** to a value greater than the number of connections supported by the SAP client library. You can increase the number of connections that the SAP client library supports by setting the environment variable, CPIC_MAX_CONV. You must reboot your computer after setting this variable for the change to take effect.

- **RfcAllowStartProgram** binding property: Specifies the external programs that the RFC client library can start, if required by an RFC partner. For example, if you are invoking an RFC that internally invokes a program on the computer running the adapter client, you must specify the name of that program for this binding property.

  - **Category**: Connection
  - **.NET Type**: String

  What you need to know:
  
  - If you are specifying multiple programs for this binding property, they must be separated by a semi-colon. For example, if you want to specify the `sapftp` and `saphttp` programs, you must specify them as `sapftp;saphttp`.
  - Also, make sure the following conditions are met:

    - The external program required by the RFC is available on the computer running the adapter client.
    - The location of the external program is present in the PATH variable on the computer running the adapter client.

  For example, BAPI_DOCUMENT_CHECKOUTVIEW2 internally executes a program, `sapftp`. So, while invoking this RFC, you must set the **RfcAllowStartProgram** binding property to `sapftp`. You must also ensure that the `sapftp` program is available locally, and the location of the `sapftp` program is added to the PATH variable on the computer running the adapter client.

- **ConnectorType** binding property: Choose to connect to SAP using classic RFC, or use the SAP Connector for .NET (NCo).

  - **Category**: ConnectorType
  - **.NET Type**: 

- **EnablePerformanceCounters** binding property: Specifies whether to enable the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] performance counters and the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] LOB Latency performance counter. The default is **false**; performance counters are disabled. The LOB Latency performance counter measures the total time spent by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in making calls to the SAP system.

  - **Category**: Diagnostics
  - **.NET Type**: bool (System.Boolean)

  **EnablePerformanceCounters** is a static property within an application domain (app domain) for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] performance counters, but it is an instance property for the adapter's LOB Latency performance counter. This means that changing **EnablePerformanceCounters** for a binding instance in an app domain will:

  - Enable or disable the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] performance counters for all objects created from all binding instances within the same app domain.
  - Enable or disable the adapter's LOB Latency performance counter only for objects created from that binding instance after the change is made.

- **AutoConfirmSentIdocs** binding property: Specifies whether the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] auto-commits tRFC client calls used for sending IDocs. The default is **false**; auto-commit is disabled. If auto-commit is disabled, the client application must explicitly commit the tRFC call by invoking the **RfcConfirmTransID** operation. The **RfcConfirmTransID** operation is a special operation surfaced by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. It appears under the TRFC node when you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].

  - **Category**: Idoc
  - **.NET Type**: bool (System.Boolean)

- **PadReceivedIdocWithSpaces** binding property: Specifies whether each line returned by the ReceiveIdoc operation is padded with spaces to the correct length. The default is false; lines are not padded.

  - **Category**: Idoc
  - **.NET Type**: bool (System.Boolean)

- **EnableSafeTyping** binding property: Enables or disables safe typing. The default is **false**; safe typing is disabled. This feature controls how the adapter surfaces certain SAP data types. For more information about safe typing, see [Basic SAP Data Types](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md). 

  - **Category**: Metadata
  - **.NET Type**: bool (System.Boolean)

- **FlatFileSegmentIndicator** binding property: Specifies whether the \<appinfo\> tag should contain segment types or segment definitions for parsing flat file IDocs. Note that the XML schema elements, however, should always contain segment definition names only.

  - **Category**: Metadata
  - **.NET Type**: enum Microsoft.Adapters.SAP.FlatFileSegmentIndicator

  There are two possible values for the **FlatFileSegmentIndicator** property:

  - **SegmentDefinition** (default) indicates that the flat files should contain the Segment Definition for each Segment in the IDoc.
  - **SegmentType** indicates that the flat files should contain the Segment Type for each Segment in the IDoc.

- **GenerateFlatfileCompatibleIdocSchema** binding property: Specifies whether flat file \<appinfo\> tags should be added to the IDoc message schema. This is required by the BizTalk flat file parser. The default is **true**, which specifies that \<appinfo\> tags will be added to the schema.

  - **Category**: Metadata
  - **.NET Type**: bool (System.Boolean) 

- **ReceiveIDocFormat** binding property: Specifies the XML format of the messages dispatched by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to the client application on the inbound side (SAP to adapter). 

  - **Category**: Metadata
  - **.NET Type**: enum Microsoft.Adapters.SAP.IdocReceiveFormat

  There are three possible values for the **ReceiveIDocFormat** property:
  
  - **String** specifies that the IDoc message should be represented as a single, string field in the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] message.
  - **Typed** (default) specifies that the IDoc message should be parsed and represented as a strongly-typed [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] message.
  - **Rfc** specifies that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] should pass the incoming RFC call as a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] message with RFC parameters.

- **UseNCoConnectionPoolSettings** binding property: Enables the control of SAP .NET Connector (NCo) connection pool parameters at a finer granularity. This property indicates whether the values that are assigned to **NCoPoolSize** and **MaxPoolWaitTime** should override the default values that are set by the adapter based on the WCF connection pool configuration properties. By default, it is set to **false**. If set to **true**, the new SAP NCo connection pool properties override the default values that are set by the adapter, and the IDLE_TIMEOUT and IDLE_CHECK_TIME NCo client parameters will be set to the **IdleConnectionTimeout** value.

  - **Category**: SAP NCo Connection Pool
  - **.NET Type**: bool (System.Boolean)

- **NCoPoolSize** binding property: Corresponds to the POOL_SIZE SAP NCo client connection parameter. It represents the maximum number of SAP NCo connections that are kept in the NCo connection pool. By default, it is set to the same value as the **MaxConnectionsPerSystem** property in the **Connection** category.

  - **Category**: SAP NCo Connection Pool
  - **.NET Type**: int (System.Int32)

- **MaxPoolWaitTime** binding property: Corresponds to the MAX_POOL_WAIT_TIME SAP NCo connection parameter. It represents the maximum amount of time in milliseconds that an NCo connection request waits after the peak connection limit is reached. By default, it is set to 0 milliseconds.

  - **Category**: SAP NCo Connection Pool
  - **.NET Type**: int (System.Int32)

- **SncLibrary** binding property: Specifies the location of the SNC library on your computer. If the PATH environment variable contains the directory in which the library resides, you only have to supply the filename of the library; otherwise you must supply the full path. The **SncLibrary** binding property surfaces an SAP connection property. For more information see the SAP documentation.

  You must set the UseSnc parameter in the connection URI to enable Secure Network Communications (SNC). For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).

  - **Category**: SNC
  - **.NET Type**: string

- **SncPartnerName** binding property: Specifies the SNC partner name. The **SncPartnerName** binding property surfaces an SAP connection property. For more information, see the SAP documentation.

  You must set the UseSnc parameter in the connection URI to enable Secure Network Communication (SNC). For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).

  - **Category**: SNC
  - **.NET Type**: string

- **TidDatabaseConnectionString** binding property: Specifies the database connection string for the SQL Server database that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses to store Transaction Ids (TIDs). The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] setup wizard installs some SQL scripts that must be run by the SQL Server administrator against an existing database to create the SQL Server objects that are used by the adapter to store TIDs to enable inbound transactional RFC (tRFC) server calls. For more information about the SQL scripts, refer to the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation guide available at *\<installation drive\>*:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.

  - **Category**: TrfcServer
  - **.NET Type**: string

  What you need to know:
  
  - You must set this property to enable inbound tRFC server calls for receiving IDocs or RFCs from SAP. The default is **null**; tRFC server calls are not enabled.
  - You can specify the connection string in the following format: `Data Source=<myServerAddress>;Initial Catalog=<myDataBase>;User Id=<myUsername>;Password=<myPassword>;`
  - To specify the connection string, click the ellipsis button **(…)** against the binding property and enter the values for the required connection string properties.

- **AcceptCredentialsInUri** binding property: Specifies whether the SAP connection URI can contain user credentials for the SAP system. The default is **false**, which disables user credentials in the connection URI. If **AcceptCredentialsInUri** is **false** and the SAP connection URI contains user credentials, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] throws an exception. You can set **AcceptCredentialsInUri** to **true** if you must specify credentials in the URI. For more information, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).

  - **Category**: Not surfaced by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].
  - **.NET Type**: bool (System.Boolean)

## How Do I Set SAP Binding Properties?  
 You can set the SAP binding properties when you specify a connection to an SAP system. For information about how to set binding properties when you:  

- Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], see [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  

  > [!IMPORTANT]
  >  While using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], if you do not specify a value for a binding property of type string and whose default value is null then that binding property will not be available in the binding file (an XML file) or the app.config file respectively. You must manually add the binding property and its value in the binding file or the app.config file, if required.  

- Configure a send port or receive port (location) in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, see [Manually configure a physical port binding to the SAP adapter](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).  

- Use the WCF channel model in a programming solution, see [Create a channel using SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md).  

- Use the WCF service model in a programming solution, see [Configure a client binding for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).  

- Use the WCF ServiceModel Metadata Utility Tool (svcutil.exe), see [Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md).  

## See Also  
[Develop your SAP applications](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)
