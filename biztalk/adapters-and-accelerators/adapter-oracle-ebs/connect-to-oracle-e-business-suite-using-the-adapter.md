---
title: "Connect to Oracle E-Business Suite using the adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80ff31d4-be4c-42d7-a321-8f01b40dd71e
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to Oracle E-Business Suite using the adapter
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] uses ODP.NET 11.1.0.7 to connect to Oracle E-Business Suite. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] requires adapter clients to provide a connection string, called the connection Uniform Resource Identifier (URI), to connect to the Oracle E-Business Suite. Internally, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] connects to the underlying Oracle database through the URI. With a connection URI, adapter clients can specify connection parameters to connect to an external system.  

## Connectivity to Oracle EBS  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] enables adapter clients to connect to Oracle E-Business Suite in the following two ways:  
  
- **Using tnsnames.ora**: The connection URI provided by the adapter client contains only the net service name specified in the tnsnames.ora file. The adapter extracts the connection parameters such as server name, service name, and port number from the net service name entry in the tnsnames.ora file. To use this approach, the computer running the Oracle client must be configured to include the net service name for the Oracle database in the tnsnames.ora file.  
  
  > [!IMPORTANT]
  >  Due to an Oracle Client limitation, the **DataSourceName** parameter (net service name) in the [Create the SQL Server connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md) cannot contain more than 39 characters if you are performing operations in a transaction. Therefore, make sure that the value specified for the **DataSourceName** parameter is less than or equal to 39 characters if you will be performing operations in a transaction.  
  
- **Without using tnsnames.ora**: The connection URI provided by the adapter clients contains the connection parameters such as server name, service name, and port number. In this case, the net service name in the tnsnames.ora file, or the actual tnsnames.ora file itself, does not need to be present on the client computer. This is helpful when you have a large number of users connecting to the Oracle database in your organization, and adding/updating servers does not lead to manually adding/updating the connection details in the tnsnames.ora file on every client computer.  
  
  > [!IMPORTANT]
  >  This mode of connectivity is not supported if you are performing operations in a transaction. This is due to a limitation of Oracle Client.  
  
  For more information about connecting to Oracle E-Business Suite, see [Create a Connection to the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md).  
  
  Make sure you comply with the security guidelines when establishing a connection with Oracle E-Business Suite. See [Secure your Oracle EBS application](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md).
  
## Enter client credentials  
 In [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], you can provide credentials to connect to Oracle E-Business Suite in the following two places:  
  
- On the **Security** tab in the **Configure Adapter** dialog box. You can find this dialog box in the  [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
- In the **OracleUserName** and **OraclePassword** binding properties on the **Binding Properties** tab in the **Configure Adapter** dialog box. You can find this dialog box in the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], or [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. In this case, the credentials are stored in plain text in the binding file.  
  
  The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the **ClientCredentialType** binding property that allows you to specify the set of credentials (Oracle E-Business Suite or Oracle database) that will be used to connect to Oracle E-Business Suite.  
  
- To connect using the Oracle database credentials, specify the **ClientCredentialType** binding property as **Database**, and then, on the **Security** tab, specify the database credentials in the **User name** and **Password** text boxes.  If you will be performing operations on any of the Oracle E-Business Suite artifacts (interface table, interface view, concurrent program, request set, or Oracle E-Business Suite PL/SQL APIs), you must also provide the Oracle E-Business Suite credentials in the **OracleUserName** and **OraclePassword** binding properties.  
  
- To connect using Oracle E-Business Suite credentials, specify the **ClientCredentialType** binding property as **EBusiness**, and then specify Oracle E-Business Suite credentials in the **User name** and **Password** text boxes on the **Security** tab. You must also specify the Oracle database credentials for the **OracleUserName** and **OraclePassword** binding properties.  
  
  For more information about specifying client credentials, see [Configure the sign-in Credentials for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-sign-in-credentials-for-the-oracle-e-business-suite.md).  
  
## Using Windows authentication  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports Windows Authentication while connecting to Oracle E-Business Suite. With Windows Authentication, the adapter clients can determine a user’s identity based on Windows logon credentials, and can leverage the built-in security of the Windows environment. For information about connecting to Oracle E-Business Suite by using Windows Authentication, see [Connect  to Oracle E-Business Suite Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md).  
  
## See Also  
[Understand BizTalk Adapter for Oracle E-Business Suit](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)