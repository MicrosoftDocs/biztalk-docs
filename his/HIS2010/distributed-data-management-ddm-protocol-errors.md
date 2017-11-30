---
title: "Distributed Data Management (DDM) Protocol Errors | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3db8c7a7-6762-4766-95f5-901dbb38b514
caps.latest.revision: 5
---
# Distributed Data Management (DDM) Protocol Errors
The following table lists DDM protocol error constants, values, SqlState, SqlCode and a description of the error.  
  
||||||  
|-|-|-|-|-|  
|**Const**|**Value**|**SqlState**|**SqlCode**|**Description**|  
|DB2OLEDB_ERROR|-1|08S01|-1|**Message**: Internal network library error.<br /><br /> **Reason**: The client could not open a connection or execute a command due to a problem with configuration, command syntax, or other issue.<br /><br /> **Action**: Verify the connection information and check the command syntax.|  
|DB2OLEDB_ERROR_SEND|-2|08S01|-2|**Message**: Unable to send data to the host. Either the connection is lost or the network is not functioning.<br /><br /> **Reason**: The server closed the client connection.<br /><br /> **Action**: Contact the network administrator or server administrator.|  
|DB2OLEDB_ERROR_RECEIVE|-3|08S01|-3|**Message**: Error receiving data from host.<br /><br /> **Reason**: The server is unavailable or the server has closed the client connection.<br /><br /> **Action**: Contact the network administrator or server administrator.|  
|DB2OLEDB_INVALID_POINTER|-4|08S01|-4|**Message**: One of the parameters contains an invalid pointer.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the DB2 server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm.|  
|DB2OLEDB_INVALID_PARAM|-5|08S01|-5|**Message**: One of the parameters contains an invalid value.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**:  Verify that the command syntax and parameter data values are within the limits supported by the DB2 server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm.|  
|DB2OLEDB_INVALID_DATA|-6|08S01|-6|**Message**: Data is invalid.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the DB2 server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm.|  
|DB2OLEDB_INVALID_CONVERSION|-7|08S01|-7|**Message**: Invalid data conversion.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the DB2 server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm.|  
|DB2OLEDB_INVALID_USER|-8|08S01|-8|**Message**: Invalid user ID or password.<br /><br /> **Reason**: The server cannot authenticate the user with the credentials presented at connection.<br /><br /> **Action**: Verify connection information to ensure the User Name (User Identifier), Password, and Security Method specified (Interactive sign-on security, Single sign-on, or Kerberos) match the server requirements defined for the current user. For more information, see topics on User Name, Password, and Security Method, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_ERROR_WRITE|-9|08S01|-9|**Message**: Error writing local file.|  
|DB2OLEDB_ERROR_READ|-10|08S01|-10|**Message**: Error reading local file.|  
|DB2OLEDB_FILE_NOT_FOUND|-11|08S01|-11|**Message**: File not found.|  
|DB2OLEDB_INDEX_NOT_FOUND|-12|08S01|-12|**Message**: Index not found.|  
|DB2OLEDB_RECORD_NOT_FOUND|-13|08S01|-13|**Message**: Record not found.|  
|DB2OLEDB_KEY_NOT_FOUND|-14|08S01|-14|**Message**: Key not found.|  
|DB2OLEDB_INVALID_FORMAT|-15|08S01|-15|**Message**: Invalid format.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the DB2 server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm.|  
|DB2OLEDB_MAX_CONNECTIONS|-16|08S01|-16|**Message**: Maximum number of connections has been reached.<br /><br /> **Reason**: The client failed to connect to the server when all client connection resources were in use.<br /><br /> **Action**: Close unused client connections. Utilize client connection pooling. Configure a larger max pool size and set a timeout on the pooled connections. For more information, see topic on Connection Pooling, at ms-help://MS.HIS.2010/HIS2010/html/9e844d5c-d177-41d4-9489-2a29b919efcf.htm#adv8. For more information, see topic on Max Pool Size, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm#All.|  
|DB2OLEDB_NOT_CONNECTED|-17|08S01|-17|**Message**: Not connected to the host.<br /><br /> **Reason**: The server closed the client connection.<br /><br /> **Action**: Contact the network administrator or server administrator.|  
|DB2OLEDB_NETWORK_ERROR|-18|08S01|-18|**Message**: A network error occurred while connecting to the host.<br /><br /> **Reason**: The client failed to connect to DB2 server using an SNA APPC network connection with an invalid user-specified value for APPC Local LU Name.<br /><br /> **Action**:  Verify connection information to ensure the APPC Local LU Name value matches Host Integration Server SNA Service APPC Local LU Name. For more information, see topic on APPC Local LU Name, at ms-help://MS.HIS.2010/HIS2010/html/7478b857-6095-4905-a0ae-00b8733e71c5.htm.|  
|DB2OLEDB_INVALID_DATASOURCE|-19|08S01|-19|**Message**: Invalid data source name.|  
|DB2OLEDB_ACCESS_DENIED|-20|08S01|-20|**Message**: Access denied.|  
|DB2OLEDB_FILE_NOT_OPENED|-21|08S01|-21|**Message**: File is not opened.|  
|DB2OLEDB_MEMORY_ALLOC|-22|08S01|-22|**Message**: Memory allocation error.|  
|DB2OLEDB_DATA_NOT_FOUND|-23|08S01|-23|**Message**: Data not found.|  
|DB2OLEDB_INDEX_EXISTS|-24|08S01|-24|**Message**: Index already exists.|  
|DB2OLEDB_FUNCTION_NOT_SUPPORTED|-25|08S01|-25|**Message**: Function not supported.|  
|DB2OLEDB_NO_CACHE|-26|08S01|-26|**Message**: No cache.|  
|DB2OLEDB_FILE_LENGTH|-27|08S01|-27|**Message**: File length.|  
|DB2OLEDB_INVALID_CONN_ID|-28|08S01|-28|**Message**: Invalid connection ID.|  
|DB2OLEDB_INVALID_FILE_ID|-29|08S01|-29|**Message**: Invalid file ID.|  
|DB2OLEDB_INVALID_FILENAME|-30|08S01|-30|**Message**: Invalid filename.|  
|DB2OLEDB_LOCAL_FILE_ERROR|-31|08S01|-31|**Message**: Error processing local file.|  
|DB2OLEDB_INVALID_VIEW_ID|-32|08S01|-32|**Message**: Invalid view ID.|  
|DB2OLEDB_INVALID_VIEW|-33|08S01|-33|**Message**: Invalid view. Check if the view is an index file of the base file.|  
|DB2OLEDB_DISK_FULL|-34|08S01|-34|**Message**: Disk is full.|  
|DB2OLEDB_DEST_FILE_CHANGED|-35|08S01|-35|**Message**: Destination file is changed after last access.|  
|DB2OLEDB_FTX_FAILED|-36|08S01|-36|**Message**: File transfer failed.|  
|DB2OLEDB_FTX_ABORTED_BY_HOST|-37|08S01|-37|**Message**: File transfer is aborted by host.|  
|DB2OLEDB_CONNECTION_LOST|-38|08S01|-38|**Message**: Connection lost.<br /><br /> **Reason**: The server closed the client connection.<br /><br /> **Action**: Contact the network administrator or server administrator.|  
|DB2OLEDB_CONNECTION_BUSY|-39|08S01|-39|**Message**: Connection is busy.<br /><br /> **Reason**: The server is unavailable or the server has closed the client connection.<br /><br /> **Action**: Contact the network administrator or server administrator.|  
|DB2OLEDB_HOST_NOT_RESPONDING|-40|08S01|-40|**Message**: Host is not responding.<br /><br /> **Reason**: The server is unavailable or the server has closed the client connection.<br /><br /> **Action**: Contact the network administrator or server administrator.|  
|DB2OLEDB_INVALID_DATA_CONV|-41|08S01|-41|**Message**: Invalid data conversion.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**:  Verify that the command syntax and parameter data values are within the limits supported by the DB2 server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm.|  
|DB2OLEDB_DATA_TYPE_NOT_SUPPORTED|-42|08S01|-42|**Message**: Data type is not supported.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the DB2 server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm.|  
|DB2OLEDB_TIMEOUT|-43|08S01|-43|**Message**: Timeout.<br /><br /> **Reason**: The client failed to execute a command as requested by the program when a command or connection timeout expired.<br /><br /> **Action**: Configure a larger value for command timeout, connection timeout, or pooled connection timeout. For more information, see topic on Command Timeout, Connection Timeout, and Connection Pooling, at ms-help://MS.HIS.2010/HIS2010/html/9e844d5c-d177-41d4-9489-2a29b919efcf.htm#adv8.|  
|DB2OLEDB_DDMAGENT_NOT_LOADED|-44|08S01|-44|**Message**: DDM Agent is not loaded or unreachable.<br /><br /> **Reason**: The client failed to execute a command as requested by the program, when the client could not load a runtime client library or communicate with a runtime client service instance.<br /><br /> **Action**: Re-start the client program. Repair the client product installation. Contact the client administrator.|  
|DB2OLEDB_COMPONENT_MISSING|-45|08S01|-45|**Message**: Missing one of the components (DLL or EXE).<br /><br /> **Reason**: The client failed to execute a command as requested by the program, when the client could not load a component library.<br /><br /> **Action**: Re-start the client program. Repair the client product installation. Contact the client administrator.|  
|DB2OLEDB_DCONV_DLL_NOT_FOUND|-46|08S01|-46|**Message**: Data conversion (MSEIDT.DLL) not found.<br /><br /> **Reason**: The client failed to execute a command as requested by the program, when the client could not load a data conversion library.<br /><br /> **Action**: Re-start the client program. Repair the client product installation. Contact the client administrator.|  
|DB2OLEDB_INVALID_STMT_HANDLE|-47|08S01|-47|**Message**: Invalid statement handle.|  
|DB2OLEDB_VALUE_NOT_SUPPORTED|-48|08S01|-48|**Message**: Value not supported.<br /><br /> **Reason**: The client failed to execute a command as requested by the program.<br /><br /> **Action**: Verify that the command syntax and parameter data values are within the limits supported by the DB2 server platform and version. For more information on command and data type limits, see topic on Data Type Mappings, at ms-help://MS.HIS.2010/HIS2010/html/cca7e3a6-6160-48ca-89d2-90318900807f.htm.|  
|DB2OLEDB_INTERNAL_ERROR|-50|08S01|-50|**Message**: An internal error has occurred|  
|DB2OLEDB_TOO_MANY_STATEMENTS|-51|08S01|-51|**Message**: The maximum number of statements for a connection has been exceeded.<br /><br /> **Reason**: The client failed to execute a command as requested by the program, when all of the command and connection resources were in use.<br /><br /> **Action**: Close unused client connections. Utilize client connection pooling. Specify a timeout value for pooled connections. Specify a timeout value for commands. For more information, see topic on Connection Pooling, at ms-help://MS.HIS.2010/HIS2010/html/9e844d5c-d177-41d4-9489-2a29b919efcf.htm#adv8.|