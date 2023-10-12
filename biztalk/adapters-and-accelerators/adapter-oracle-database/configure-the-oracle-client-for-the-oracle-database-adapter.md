---
description: "Learn more about: Configure the Oracle Client for the Oracle Database adapter"
title: "Configure the Oracle Client for the Oracle Database adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configure the Oracle Client for the Oracle Database adapter
> [!IMPORTANT]
>  This topic is relevant only if you are using tnsnames.ora to connect to the Oracle database.  
  
 The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] connects to the Oracle database through the Oracle client installed on your computer. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] passes the net service name that you specify in the connection URI to the Oracle client to establish a connection to the Oracle database. The net service name is an alias that the Oracle client uses to acquire connection information for the target Oracle database service.  
  
 The Oracle client resolves the net service name according to the naming method that it is configured to use. You use the Oracle Net Configuration Assistant to configure the naming methods to be used by the Oracle client. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports the Local Naming method for connecting to the Oracle database. This method uses a local file, tnsnames.ora, to resolve the net service name.  
  
 The tnsnames.ora file associates net service names with connect descriptors that contain the information the Oracle client needs to establish a connection to a specific Oracle database service (instance). The following is a sample entry from tnsnames.ora.  
  
```  
ADAPTER =  
  (DESCRIPTION =  
    (ADDRESS_LIST =  
      (ADDRESS = (PROTOCOL = TCP)(HOST = yourOracleServer)(PORT = 1521))  
    )  
    (CONNECT_DATA =  
      (SERVICE_NAME = yourOracleDatabaseServiceName)  
    )  
  )  
```  
  
 In this sample entry, ADAPTER is the net service name. The connect descriptor specifies address information and the service name of the Oracle database service associated with ADAPTER. You can use the Oracle Net Configuration Assistant to create and configure net service names in tnsnames.ora. After you have configured the net service name, you can specify it in a connection URI as in the following example.  
  
```  
oracledb://ADAPTER  
```  
  
 For more information about using the Oracle Net Configuration Assistant and about tnsnames.ora, see the Oracle Database Net Services Administrator's Guide. Consult your database administrator about configuration details for your specific installation.  
  
## See Also  
[Create a connection to the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)
