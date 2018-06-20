---
title: "Create the Siebel system connection URI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection URI"
  - "connecting to Siebel, using the connection URI"
  - "how to, connect using connection URI"
  - "connecting using connection URI"
ms.assetid: 8cc78149-1c20-40db-aece-aab520ee04e7
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create the Siebel system connection URI
The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] connection URI contains properties that the adapter uses to establish a connection to the Siebel system.  

 This topic provides information about the Siebel connection URI and also provides links to other topics that explain how to specify a connection URI in different programming scenarios.  

## Connection URI for the Siebel Adapter  
 A typical [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] endpoint address URI is represented as follows:  

```  
scheme://userinfoparams@hostinfoparams?query_string  
```  

 The endpoint address URI contains the following components:  

- scheme is the scheme name.  

- userinfoparams is a name-value collection of parameters required for user authentication by the endpoint.  

- hostinfoparams is information required to establish the connection to the host; for example, a path.  

- query_string is an optional name-value collection of parameters delimited by a question mark (?).  

  The Siebel connection URI follows this general format and is implemented as follows:  

```  
siebel://Username=[USER_NAME];Password=[PASSWORD]@[SERVER]:[PORT]?SiebelObjectManager=[SIEBEL_OBJECT_MANAGER_NAME]&SiebelEnterpriseServer=[SERVER_NAME]&Language=[LANGUAGE]&Transport=[TRANSPORT]&Encryption=[ENCRYPTION]&Compression=[COMPRESSION]&SiebelServer=[SIEBEL_SERVER_NAME]&SiebelRepository=[SIEBEL_REPOSITORY_NAME]  
```  

 The following sections describe the properties implemented for each component of the Siebel connection URI.  

### The Scheme for the Siebel Connection URI  
 The scheme for the Siebel connection URI is "siebel".  

### User Information in the Siebel Connection URI  
 By default, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] throws an exception when Siebel system credentials are specified in the connection URI. This is because these credentials are represented as plain text, which poses an inherent security risk. You can set the **AcceptCredentialsInUri** binding property to control whether the connection URI can contain credentials. If the **AcceptCredentialsInUri** property is **false**, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] throws an exception if the connection URI contains credentials; if the property is **true**, no exception is thrown.  

> [!IMPORTANT]
>  Due to the inherent security risks posed by passing credentials in strings as plain text, it is best not to specify Siebel system credentials in the connection URI.  

 There are several ways to supply Siebel system credentials without specifying them in the connection URI.  

- In code, you can set the **ClientCredentials** property on the appropriate object.  

- When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], you can enter the credentials by selecting the **Security** tab of the **Configure Adapter** dialog box.  

- When you specify a send port or receive location binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, you can enter the credentials by selecting the **Security** tab of the appropriate dialog box.  

  The user information (userinfoparams) in the Siebel connection URI is represented as a name-value collection of parameters required for user authentication. The following table describes these parameters.  

| Property |                                                                                                                                                                                                          Description                                                                                                                                                                                                          |
|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Username |      The user name on the Siebel system; this value is case-sensitive. You must set the **AcceptCredentialsInUri** binding property to **true** to specify the user name and password in the connection URI. **Note:**  The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the Siebel system.       |
| Password | The password for the user on the Siebel system; this value is case-sensitive. You must set the **AcceptCredentialsInUri** binding property to **true** to specify the user name and password in the connection URI. **Note:**  The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the Siebel system. |

### Host Information in the Siebel Connection URI  
 The Siebel host information (hostinfoparams) specifies the address of the Siebel system in the following format: [SERVER]:[PORT]. Depending on the Siebel server version, the Siebel host information takes different values:  

- **For Siebel version 7.5 and earlier**, the host information parameter takes the name of the computer on which Siebel gateway server is installed and the Siebel gateway port number.  

- **For Siebel version 7.7 and later**, the host information parameter takes the name of the computer on which the Siebel server is installed and the Siebel connection broker port number.  

  > [!IMPORTANT]
  >  When you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to connect to a Siebel system, the host information must be provided for the “SiebelGateway” connection property.  

### Query Information in the Siebel Connection URI  
 The query information (query_string) in the Siebel connection URI is used to specify additional connection properties.  


|        Property        |                                                                                                                                          Description                                                                                                                                           |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  SiebelObjectManager   |                                                                                                  The name of the Siebel object manager on the enterprise server. This parameter is required.                                                                                                   |
| SiebelEnterpriseServer |                                                                                                             The name of the Siebel Enterprise Server. This parameter is required.                                                                                                              |
|        Language        |                                             The language of the object manager. This parameter is optional. If it is not specified, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] supplies a default value (enu).                                              |
|       Transport        |                                                                        The transport; only tcpip is supported. This parameter is optional. If it is not specified, the Siebel system supplies a default value (tcpip).                                                                         |
|       Encryption       | The type of encryption to use between the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and the Siebel system. Supported values are none, mscrypto, or rsa. This parameter is optional. If it is not specified, the Siebel system supplies a default value (none). |
|      Compresssion      |    The compression algorithm to use between the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] and the Siebel system. Supported values are none or zlib. This parameter is optional. If it is not specified, the Siebel system supplies a default value (zlib).     |
|      SiebelServer      |                                                                                 The Siebel server. Required for all Siebel 7.5 server connections (7.5.2, 7.5.3, etc.); otherwise, do not set this parameter.                                                                                  |
|    SiebelRepository    |                          The Siebel repository. Required if more than one repository exists on the server; otherwise, optional. **Note:**  If more than one repository exists on the server, you must specify a target repository in the SiebelRepository parameter.                           |

 For more information about the Siebel parameters that are set in the query information, see your Siebel documentation.  

## Using Reserved Characters in the Connection URI  
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not support specifying a connection URI that has special characters for any of the parameter values. If the connection parameter values contain special characters, make sure you do one of the following:  

- If you are specifying the URI in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters. If you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  

- If you are specifying the URI while creating a send or receive port in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  

## Using the Connection URI to Connect to the Siebel System  
 The following is a sample Siebel connection URI.  

```  
siebel://Username=YourUserName;Password=YourPassword@Siebel_server:1234?SiebelObjectManager=obj_mgr&SiebelEnterpriseServer=entserver&Language=enu  
```  

> [!NOTE]
>  This sample URI contains the Siebel system credentials; you must set the **AcceptCredentialsInUri** binding property to **true** to use a connection URI that contains credentials.  

 For information about how to establish a connection to the Siebel system (including setting connection properties) when you:  

- Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], see [Get Metadata for Siebel Operations in Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  

- Configure a send port or receive port (location) in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, see [Manually configure a physical port binding to the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md).

- Use the WCF channel model in a programming solution, see [Create a channel using Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-channel-using-siebel.md).  

- Use the WCF service model in a programming solution, see [Configure a WCF Client for a Siebel System](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md).  

- Use the WCF ServiceModel Metadata Utility Tool (svcutil.exe), see [Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md).  

## See Also  
 [Create a connection to the Siebel system](../../adapters-and-accelerators/adapter-siebel/create-a-connection-to-the-siebel-system.md)   
[Develop your Siebel applications](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)   
 [Develop Siebel Applications Using the WCF Channel Model3](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md)   
 [Develop SQL applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)