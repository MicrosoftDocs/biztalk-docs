---
title: "Create the SAP system connection URI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection URI"
  - "how to, connect using connection URI"
  - "connecting using connection URI"
  - "connecting to SAP, using the connection URI"
ms.assetid: e41ed488-07a7-4fb7-97c0-6d626e041e95
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create the SAP system connection URI
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] connection URI contains properties that the adapter uses to establish a connection to the SAP system.  

> [!IMPORTANT]
>  By default, the SAP client library (librfc32u.dll) supports a maximum of 100 connections to the SAP system. If you exceed this number of connections, an exception will be thrown. For this reason, you should either set the **MaxConnectionsPerSystem** binding property to limit the number of connections that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] will try to open on the SAP system; or set the CPIC_MAX_CONV environment variable to increase the number of connections supported by the SAP client library. If you change CPIC_MAX_CONV, you must restart your computer for the change to take effect. For more information about the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  

 This topic provides information about the SAP connection URI and also provides links to other topics that explain how to specify a connection URI in different programming scenarios.  

## Connection URI for the SAP Adapter  
 A typical [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] endpoint address URI is represented as follows:  

```  
scheme://userinfoparams@hostinfoparams?query_string  
```  

 The endpoint address URI contains the following components:  

- scheme is the scheme name.  

- userinfoparams is a name-value collection of parameters required for user authentication by the endpoint.  

- hostinfoparams is information required to establish the connection to the host; for example, a path.  

- query_string is an optional name-value collection of parameters delimited by a question mark (?).  

  The endpoint address URI that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses for a SAP system is specified by using a SAP connection URI. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] implements this connection URI as follows:  

```  
sap://user=[USER_NAME];passwd=[PASSWORD];Client=[CLIENT];lang=[LANGUAGE];[UseSnc]=[True|False]@connectiontype/conndetail1/conndetail2?GwHost=[GWHOST]?GwServ=[GWSERV]?MsServ=[MSSERV]?Group=[GROUP]?ListenerDest=[LISTENERDEST]?ListenerGwHost=[LISTENERGWHOST]?ListenerGwServ=[LISTENERGWSERV]?ListenerProgramId=[LISTENERPROGRAMID]?RfcSdkTrace=[true/false]?AbapDebug=[true/false]  
```  

 The components of the connection URI are explained in the following sections.  

### The SAP Connection URI scheme  
 The scheme for the SAP connection URI is "sap".  

### User Information in the SAP Connection URI  
 The user information (userinfoparams) in the SAP connection URI is represented as a name-value collection of parameters required for user authentication, client identification, and language specification. The following table describes these parameters.  


| Property |                                                                                                                                                                                                                                                                                                                                                                                                          Description                                                                                                                                                                                                                                                                                                                                                                                                          |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   User   |                                                                                                                                                                                                            The user name on the SAP system; this value is case sensitive. You must set the **AcceptCredentialsInUri** binding property to **true** to specify the user name and password in the connection URI. **Note:**  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the SAP system.                                                                                                                                                                                                             |
|  Passwd  |                                                                                                                                                                                                       The password for the user on the SAP system; this value is case sensitive. You must set the **AcceptCredentialsInUri** binding property to **true** to specify the user name and password in the connection URI. **Note:**  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the SAP system.                                                                                                                                                                                                       |
|  Client  |                                                                                                                                                                                                                                                                                                                                                                                                   The SAP system client id.                                                                                                                                                                                                                                                                                                                                                                                                   |
| Language |                                                                                                                                                                                                                                                                                                                                                                                                           Language.                                                                                                                                                                                                                                                                                                                                                                                                           |
|  UseSnc  | Optional parameter that specifies whether SAP Secure Network Communications (SNC) is enabled. The value can be True or False; if True, SNC is enabled. The default is False<br /><br /> When you enable SNC, you must also set the **SncPartnerName** and **SncLibrary** binding properties. For more information, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).<br /><br /> If SNC is enabled and the connection URI contains credentials, the adapter throws an exception. **Note:**  UseSnc connection parameter is applicable only for connection types A and B. The different connection types and their significance is described in detail later in this topic. |

> [!NOTE]
>  You must specify the Client and Language in the SAP connection URI.  

 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces the **AcceptCredentialsinUri** binding property so you can control whether SAP system credentials can be specified in the connection URI. This is because the credentials are represented as plain text in the connection URI and this poses an inherent security risk. By default, the **AcceptCredentialsInUri** binding property is false and the adapter throws an exception if credentials are specified in the connection URI.  

 There are some scenarios in which it is necessary to specify credentials in the connection URI; for example, to receive the inbound operations from the SAP system when you use the WCF service model or the WCF channel model. You can set the **AcceptCredentialsInUri** property to true for these scenarios. It is a best practice, however, to avoid providing credentials directly in the connection URI. For more information about how to more securely provide credentials for the SAP connection, see [Secure your SAP applications](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md).  

> [!IMPORTANT]
>  If you enable Secure Network Communications (SNC) by setting the UseSnc parameter to true, the adapter throws an exception.  

### Host Information in the SAP Connection URI  
 The SAP host information (hostinfoparams) is represented by the following elements in the SAP connection URI: `connectiontype/conndetail1/conndetail2`. These parameters specify details about the client connection to the SAP system. Additional details about the SAP client connection as well as details that establish a connection as a listener to an SAP RFC destination can be specified in the query_string. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following client connection types in the SAP connection URI:  

- A: An application-host based connection in which the connection URI specifies an application server through which the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] connects to SAP.  

- B: A load balanced connection in which the connection URI specifies a message server through which the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] connects to SAP.  

- D: A destination-based connection in which the connection URI specifies a destination in the saprfc.ini file that contains the connection parameters for SAP.  

  > [!NOTE]
  > Connection Type B only applies to send ports.  When configuring a receive location, choose Connection Type A or D.

  The following table describes how these connections are specified in the SAP connection URI.  

|Connection Type|Conndetail1|Conndetail2|Description|  
|---------------------|-----------------|-----------------|-----------------|  
|A|ASHOST (Application Server Host)|SYSNR (SAP System Number)|Specifies an application host-based connection. For an application host-based connection, an optional Gateway Host and Gateway Service can be specified in the query_string.|  
|B|MSHOST (Message Server Host)|R3NAME (SAP R3 Name)|Specifies a load balancing connection through a message server. For a load balancing connection, an optional server Group and Message Service can be specified in the query_string.|  
|D|DEST (Destination that contains the connection parameters in the saprfc.ini file)|--|Specifies a destination-based connection. The SAP connection parameters are contained in the specified destination in the saprfc.ini file. Only A-type and B-type connections can be specified in the destination.|  

> [!NOTE]
>  If you specify connection values in the saprfc.ini file, make sure the file is located in the same folder as the .exe accessing the file or at a standard location as required by the SAP system. For more information, see the SAP documentation.  

### Query Information in the SAP Connection URI  
 The query information (query_string) in the SAP connection URI contains optional parameters that can be included to specify the following:  

- Additional connection details for application host-based connections (A).  

- Additional connection details for load balancing connections (B).  

- Listener details that specify an RFC Destination on the SAP system through which the SAP system can send RFCs, TRFCs, and IDocs to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  

- Whether to enable SAP Secure Network Communications (SNC).  

- Details that specify debugging configuration.  

  Query parameters are optional; however, listener details must be specified for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to act as an RFC server.  

  The following table describes the query parameters and indicates the SAP connection types for which they are valid.  

|       Value       | Valid Connection Type |                                                                                                                                                                                                                                    Description                                                                                                                                                                                                                                     |
|-------------------|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      GwHost       |           A           |                                                                                                                                                                                              Specifies the name of an optional gateway host in an application host-based connection.                                                                                                                                                                                               |
|      GwServ       |           A           |                                                                                                                                                                                             Specifies the name of an optional gateway service in an application host-based connection.                                                                                                                                                                                             |
|      MsServ       |           B           |                                                                                                                                                                                                 Specifies the name of an optional message service in a load balancing connection.                                                                                                                                                                                                  |
|       Group       |           B           |                                                                                                                                                                                                 Specifies an optional group of application servers in a load balancing connection.                                                                                                                                                                                                 |
|   ListenerDest    |          (R)          |                                                                                                                                                                      Specifies an optional destination in the saprfc.ini file in an rfc server connection. The destination must specify an R-type connection.                                                                                                                                                                      |
|  ListenerGwHost   |          (R)          |                                                                                      Specifies the gateway host for an rfc server connection. This parameter is optional; however, if an rfc server connection is desired and LISTENERDEST is not specified or no gateway host is specified by the destination in the saprfc.ini file, then LISTENERGWHOST must contain a valid gateway host.                                                                                      |
|  ListenerGwServ   |          (R)          |                                                                                 Specifies the gateway service for an rfc server connection. This parameter is optional; however, if an rfc server connection is desired and LISTENERDEST is not specified or no gateway service is specified by the destination in the saprfc.ini file, then LISTENERGWSERV must contain a valid gateway service.                                                                                  |
| ListenerProgramId |          (R)          |                                                                                  Specifies the program id for an rfc server connection. This parameter is optional; however, if an rfc server connection is desired and LISTENERDEST is not specified or no gateway service is specified by the destination in the saprfc.ini file, then LISTENERPROGRAMID must contain a valid gateway service.                                                                                   |
|    RfcSdkTrace    |          All          | Optional parameter that specifies whether RFC library tracing is enabled. The value can be True or False; if True, RFC Library tracing is enabled. The default is False.<br /><br /> The level of tracing enabled by the RfcSdkTrace parameter depends upon the environment variable RFC_TRACE.<br /><br /> -   If RFC_TRACE not present, or is set to 0, then the minimum level of tracing is enabled.<br />-   You can set RFC_TRACE to 1 or 2 to increase the level of tracing. |
|     AbapDebug     |          All          |                                                                                             Optional parameter that specifies whether ABAP debugging from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] is enabled. The value can be True or False; if True, ABAP debugging is enabled. The default is False. If AbapDebug is True, the SAP GUI is opened.                                                                                             |

 The parameters in the query string are SAP parameters and their values are defined by SAP. For more information about these parameters please see your SAP documentation.  

 The following shows a sample connection URI for an application host-based connection:  

```  
sap://Client=800;lang=EN@A/YourSAPHOST/00  
```  

## Connection URI Properties in the Configure Adapter Dialog Box  
 When you connect to the SAP system with the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] you set the connection URI parameters from the **URI Properties** tab in the **Configure Adapter** dialog box. The following table shows how the URI properties are displayed in the **URI Properties** sheet. (The URI properties are listed by group in the order they appear in the URI Properties sheet.)  

|Category|URI Property|URI Part|  
|--------------|------------------|--------------|  
|Application Server|Application Server Host|Conndetail1 (host information connection type A)|  
|Application Server|Gateway Host|GwHost (query string)|  
|Application Server|Gateway Service|GwServ (query string)|  
|Application Server|System Number|Conndetail2 (host information connection type A)|  
|Destination|Destination Name|Conndetail1 (host information connection type D)|  
|Diagnostics|RFC Trace|RfcSdkTrace (query string)|  
|Diagnostics|ABAP Debug|AbapDebug (query string)|  
|Login Information|Client|Client (userinfoparams)|  
|Login Information|Language|Language (userinfoparams)|  
|Message Server|Application Server Group Name|Group (query string)|  
|Message Server|Message Server Host|Conndetail1 (host information connection type B)|  
|Message Server|Message Server Service|MsServ (query string)|  
|Message Server|R/3 System Name|Conndetail2 (host information connection type B)|  
|Misc|Connection Type|Connection Type (host information: A, B, or D)|  
|RFC Server|Destination Name|ListenerDest (query string)|  
|RFC Server|Gateway Host|ListenerGwHost (query string)|  
|RFC Server|Gateway Service|ListenerGwServ (query string)|  
|RFC Server|Program Id|ListenerProgramId (query string)|  
|SNC|UseSnc|UseSnc (user info)|  

## How to specify a Connection URI for RFC Server Connections.  
 To create an endpoint address through which the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can act as an RFC server, you must specify a SAP program id, a SAP gateway host, and a SAP gateway service that correspond to an RFC destination on the SAP system. For information about how to setup an RFC destination on SAP, see [Create an RFC, RFC destination, and send an RFC from SAP](creating-an-rfc-in-an-sap-system.md).  

 You can specify the program id, gateway host, and gateway service in the connection URI in one of two ways:  

-   by setting the ListenerGwHost, ListenerGwServ, and ListenerProgramId query parameters  

-   by setting the ListenerDest query parameter to a destination in the saprfc.ini file that specifies an R-type connection.  

> [!NOTE]
>  If you specify connection values in the saprfc.ini file, make sure the file resides at the same location as the .exe accessing the file or at a standard location as required by the SAP system. For more information, see the SAP documentation.  

 To specify a connection URI for an RFC server connection, you specify a regular client connection with an RFC destination specified in the query string, as in the following example:  

```  
sap://Client=800;lang=EN@A/YourSAPHOST/00?ListenerGwHost=YourSAPHOST&ListenerGwServ=SAPGW00&ListenerProgramId=MyProgramId  
```  

 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the information contained in the userinfoparams and hostinfoparams part of the connection URI to retrieve metadata from the SAP system and uses the information provided by the Listener parameters in the query string to register itself as a listener at the SAP RFC Destination.  

## Using Reserved Characters in the Connection URI  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support specifying a connection URI that has special characters for any of the parameter values. If the connection parameter values contain special characters, make sure you do one of the following:  

- If you are specifying the URI in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters. If you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  

- If you are specifying the URI while creating a send or receive port in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  

## Using the Connection URI to Connect to the SAP System  
 For information about how to establish a connection to the SAP system when you:  

- Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], see [Connect to the SAP System in Visual Studio](../../adapters-and-accelerators/adapter-sap/connect-to-the-sap-system-in-visual-studio.md).  

- Configure a send port or receive port (location) in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, see [Manually configure a physical port binding to the SAP adapter](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).  

- Use the WCF channel model in a programming solution, see [Create a channel using SAP](../../adapters-and-accelerators/adapter-sap/create-a-channel-using-sap.md).  

- Use the WCF service model in a programming solution, see [Configure a client binding for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).  

- Use the WCF ServiceModel Metadata Utility Tool (svcutil.exe), see [Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md).  

## See Also  
 [Create a connection to the SAP system](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md)