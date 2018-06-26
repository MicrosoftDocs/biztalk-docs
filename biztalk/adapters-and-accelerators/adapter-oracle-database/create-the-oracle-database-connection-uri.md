---
title: "Create the Oracle Database connection URI | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connection URI, basic format of"
  - "connection URI, database credentials and"
  - "connection URI, connecting to the Oracle database"
  - "connection URI"
ms.assetid: 17d0a6d3-1b0c-43d6-a705-402c09a78ee0
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create the Oracle Database connection URI
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] connection URI contains properties that the adapter uses to establish a connection to the Oracle database. This topic provides information about how to specify the connection URI to connect to the Oracle database using tnsnames.ora and without using tnsnames.ora. It also provides information about using the connection URI to connect to the Oracle database.  

## Connection URI to Connect to the Oracle Database Using tnsnames.ora  

> [!IMPORTANT]
> - For this approach, you must add the net service name entry in the tnsnames.ora file on the computer with the adapter client installed. For more information about the net service name entry, see [Configure the Oracle Client for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md).  
>   -   Due to an Oracle Client limitation, the **DataSourceName** parameter (net service name) in the connection URI cannot contain more than 39 characters if you are performing operations in a transaction. Therefore, make sure that the value specified for the **DataSourceName** parameter is less than or equal to 39 characters if you will be performing operations in a transaction.  

 A typical endpoint address URI in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] is represented as: `scheme://userauthparams@hostinfoparams?query_string`, where:  

- scheme is the scheme name.  

- userauthparams is a name-value collection of parameters required for user authentication by the endpoint.  

- hostinfoparams is information required to establish the connection to the host; for example, a path.  

- query_string is an optional name-value collection of parameters delimited by a question mark (?).  

  The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] connection URI adheres to this basic format and is implemented as follows:  

```  
oracledb://User=[USER_NAME];Password=[PASSWORD]@[NET_SERVICE_NAME]?PollingId=[POLLING_ID]  
```  

 The following table explains the properties contained in the connection URI.  


| Connection URI Property |    Category    |                                                                                                                                                                                                                                                                                                                                                                                           Description                                                                                                                                                                                                                                                                                                                                                                                            |
|-------------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       [USER_NAME]       | userauthparams | The user name to use for authentication on the Oracle database; for example, SCOTT. You must set the **AcceptCredentialsInUri** binding property to **true** to specify the user name and password in the connection URI.<br /><br /> **Note** The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the Oracle database. User names on the Oracle database are case-sensitive. You should ensure that you provide Oracle user names to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in the case expected by your Oracle database. Typically, this means that the user name in the SCOTT/TIGER credential should be upper case: "SCOTT". |
|       [PASSWORD]        | userauthparams |                                                                                                                                The password to use for authentication on the Oracle database; for example, TIGER. You must set the **AcceptCredentialsInUri** binding property to **true** to specify the user name and password in the connection URI.<br /><br /> **Note** The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the Oracle database. For release 10g and earlier, passwords on the Oracle system are not case-sensitive.                                                                                                                                |
|   [NET_SERVICE_NAME]    | hostinfoparams |                                                                                                                                                                            A net service name that is specified in the tnsnames.ora file on the computer where the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is installed. For more information about net service names and tnsnames.ora, see [Configure the Oracle Client for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md).                                                                                                                                                                             |
|      [POLLING_ID]       |  query_string  |                                                                                                                                                                                                                     An optional string that should be appended by the adapter to the standard namespace of the POLLINGSTMT operation. This enables you to specify a unique namespace for each polling operation when a project contains multiple polling operations. You do not have to specify a PollingId string if your project contains only one POLLINGSTMT operation.                                                                                                                                                                                                                      |

> [!NOTE]
>  Query parameters are also used in the connection URI when an endpoint address is specified for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] Metadata Exchange client.  

## Connection URI to Connect to the Oracle Database Without Using tnsnames.ora  

> [!IMPORTANT]
> - For this approach, the net service name in the tnsnames.ora file, or the actual tnsnames.ora file itself does not need to be present on the client computer.  
>   -   This mode of connectivity is not supported if you are performing operations in a transaction. This is due to a limitation of Oracle Client.  

 A typical endpoint address URI in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] is represented as: `scheme://userauthparams@hostinfoparams?query_string`, where:  

- scheme is the scheme name.  

- userauthparams is a name-value collection of parameters required for user authentication by the endpoint.  

- hostinfoparams is information required to establish the connection to the host; for example, server name, port number, etc.  

- query_string is an optional name-value collection of parameters delimited by a question mark (?).  

  The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] connection URI adheres to this basic format and is implemented as follows:  

```  
oracledb://User=[USER_NAME];Password=[PASSWORD]@[SERVER_NAME]:[PORT_NUMBER]/[SERVICE_NAME]/SERVICE_TYPE]?PollingId=[POLLING_ID]  
```  

 The following table explains the properties contained in the connection URI.  


| Connection URI Property |    Category    |                                                                                                                                                                                                                                                                                                                                                                                           Description                                                                                                                                                                                                                                                                                                                                                                                            |
|-------------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       [USER_NAME]       | userauthparams | The user name to use for authentication on the Oracle database; for example, SCOTT. You must set the **AcceptCredentialsInUri** binding property to **true** to specify the user name and password in the connection URI.<br /><br /> **Note** The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the user name when it opens a connection on the Oracle database. User names on the Oracle database are case-sensitive. You should ensure that you provide Oracle user names to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in the case expected by your Oracle database. Typically, this means that the user name in the SCOTT/TIGER credential should be upper case: "SCOTT". |
|       [PASSWORD]        | userauthparams |                                                                                                                                The password to use for authentication on the Oracle database; for example, TIGER. You must set the **AcceptCredentialsInUri** binding property to **true** to specify the user name and password in the connection URI.<br /><br /> **Note** The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] preserves the case of the value that you enter for the password when it opens a connection on the Oracle database. For release 10g and earlier, passwords on the Oracle system are not case-sensitive.                                                                                                                                |
|      [SERVER_NAME]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                          Name of the server on which the Oracle database is running. This is mandatory.                                                                                                                                                                                                                                                                                                                                                          |
|      [PORT_NUMBER]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                The Oracle Net Listener port. If no value is specified, the adapter takes the default value 1521.                                                                                                                                                                                                                                                                                                                                                 |
|     [SERVICE_NAME]      | hostinfoparams |                                                                                                                                                                                                                                                                                                                                                                       The Oracle database service name. This is mandatory.                                                                                                                                                                                                                                                                                                                                                                       |
|     [SERVICE_TYPE]      | hostinfoparams |                                                                                                                                                                                                                                                  The type of Oracle service. The possible values are **Dedicated** or **Shared**. A dedicated service uses a dedicated server process to serve only one user process. A shared service uses a shared server process that can that can serve multiple user processes. Default is **Dedicated**.                                                                                                                                                                                                                                                   |
|      [POLLING_ID]       |  query_string  |                                                                                                                                                                                                                     An optional string that should be appended by the adapter to the standard namespace of the POLLINGSTMT operation. This enables you to specify a unique namespace for each polling operation when a project contains multiple polling operations. You do not have to specify a PollingId string if your project contains only one POLLINGSTMT operation.                                                                                                                                                                                                                      |

> [!NOTE]
>  Query parameters are also used in the connection URI when an endpoint address is specified for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] Metadata Exchange client.  

## Oracle Database Credentials and the Connection URI  
 By default, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] throws an exception when the Oracle database credentials are specified in the connection URI. This is because these credentials are represented as plain text in the connection URI, and this poses a security risk. You can set the **AcceptCredentialsInUri** binding property to control whether the connection URI can contain credentials for the Oracle database. If the **AcceptCredentialsInUri** property is **false**, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] throws an exception if the connection URI contains Oracle database credentials; if the property is **true**, no exception is thrown. There are a few limited scenarios in which it is necessary to specify credentials in the connection URI; for example, to receive the inbound POLLINGSTMT operation when you use the WCF service model or the WCF channel model. For most situations, however, you should avoid providing credentials in the connection URI. For more information about how to more securely provide credentials for the Oracle database, see [Secure your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md).  

> [!IMPORTANT]
>  Due to the security risks posed by passing credentials in strings as plain text, you should avoid specifying Oracle database connection credentials in the connection URI.  

## Using Reserved Characters in the Connection URI  
 The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] does not support specifying a connection URI that has special characters for any of the parameter values. If the connection parameter values contain special characters, make sure you do one of the following:  

- If you are specifying the URI in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] using [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], you must specify them as-is in the **URI Properties** tab, that is, without using any escape characters. If you specify the URI directly in the **Configure a URI** field and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  

- If you are specifying the URI while creating a send or receive port in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, and the connection parameters contain reserved characters, you must specify the connection parameters using proper escape characters.  

## Using the Connection URI to Connect to the Oracle Database  
 The following is an example of a connection URI for [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  

|Using tnsnames.ora|Without using tnsnames.ora|  
|------------------------|--------------------------------|  
|`oracledb://ADAPTER`<br /><br /> In this example, ADAPTER is a net service name that is associated with the SERVICE NAME and connection information for the target Oracle database in tnsnames.ora.|`oracledb://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated`<br /><br /> In this example, the server name is “yourOracleServer” and the service name is “yourOracleDatabaseServiceName”.|  

 The following is an example of a connection URI for a POLLINGSTMT operation. This URI includes a PollingId parameter to modify the namespace of the POLLINGSTMT operation.  

|Using tnsnames.ora|Without using tnsnames.ora|  
|------------------------|--------------------------------|  
|`oracledb://ADAPTER?PollingId=MyPollingNotification1`|`oracledb://yourOracleServer:1521/yourOracleDatabaseServiceName/Dedicated? PollingId=MyPollingNotification1`|  

 For the above connection URIs, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] creates the following namespace for the POLLINGSTMT operation.  

```  
http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTMyPollingNotification1  
```  

 For information about how to establish a connection to the Oracle database when you:  

- Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], see [Connect to Oracle Database in Visual Studio using the Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).  

- Configure a send port or receive port (location) in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution, see [Manually configure a physical port binding to the Oracle Database Adapter](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).  

- Use the WCF channel model in a programming solution, see [Create a channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).  

- Use the WCF service model in a programming solution, see [Configure a client binding for the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md).  

- Use the WCF ServiceModel Metadata Utility Tool (svcutil.exe), see [Using the ServiceModel Metadata Utility Tool with the BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md).  

## See Also  
[Create a connection to the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)   
 [Configure the Oracle Client for the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)