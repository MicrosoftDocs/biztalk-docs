---
title: "Configuring the FTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FTP adapters, configuring"
  - "configuring [FTP adapters]"
ms.assetid: 7e7d2e2d-142e-4459-be25-efd501b396d2
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring the FTP Adapter


## Before you begin
- The FTP adapter supports reading and writing data from a secure FTP server. The adapter provides support for file transfer from an FTP server over Secure Sockets Layer (SSL)/Transport Level Security (TLS). 
- The FTP adapter supports downloading of files from read-only file locations. 
- The FTP adapter supports atomic file transfer for ASCII mode also.

See [Best practices and recommendations for the FTP adapter](../core/best-practices-and-recommendations-for-the-ftp-adapter.md).


## Configure the receive location

You can set FTP receive location adapter properties in the BizTalk Server Administration console. If properties are not set in the receive location, then the default receive handler values in the BizTalk Server Administration console are used.  

> [!NOTE]
>  Before completing the following procedure, you must have already added a receive port. See [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  
> 1.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application in which you want to create a receive location.  

2. In the left pane, click the **Receive Ports** node. In the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.  

3. In the **Receive Port Properties** dialog box, in the left pane, select **Receive Locations**. In the right pane, double-click an existing receive location or click **New** to create a new receive location.  

4. In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **FTP** from the drop-down list and then click **Configure**.  

5. In **FTP Transport Properties**, do the following:  

   **Batch**

   |Use this|To do this|  
   |--------------|----------------|  
   |**Maximum Files**|Specify the maximum number of files per BizTalk Server batch.<br /><br /> Zero (0) indicates no limit.<br /><br /> **Default value:** 0|  
   |**Maximum Size**|Specify the maximum number of bytes per BizTalk Server batch.<br /><br /> Zero (0) indicates no limit.<br /><br /> **Default value:** 0|  

   **Firewall**

   |Use this|To do this|  
   |--------------|----------------|     
   |**Address**|Specify the address of the firewall, either a DNS name or an IP address.|  
   |**Mode**|Specify the mode in which the adapter connects to the FTP server.<br /><br /> **Valid values:** Passive and Active<br /><br /> In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br /><br /> **Default value:** Active|  
   |**Password**|Specify the password for the firewall.|  
   |**Port**|Specify the port for the firewall.<br /><br /> **Valid values:** 1 through 65535 inclusive<br /><br /> **Default value:** 21|  
   |**Type**|Specify the type of firewall deployed.<br /><br /> **Valid values:** None, Socks 4, and Socks 5<br /><br /> **Default value:** None|  
   |**User**|Specify the user name for the firewall.|  

   **FTP**


   |         Use this         |                                                                                                                                                                                                   To do this                                                                                                                                                                                                   |
   |--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |       **Account**        |                                                                                                                                                Specify the account name for the FTP server. This option is deprecated and use of this property is discouraged.                                                                                                                                                 |
   |      **After Get**       |                                                                                                                                                          Specify the FTP commands to run after the file GET. Separate commands with a semicolon (;).                                                                                                                                                           |
   |      **Before Get**      |                                                                                                                           Specify the FTP commands to run before the file GET. Separate commands with a semicolon (;). **Note:**  QUIT command is not supported before the file GET.                                                                                                                           |
   |   **Error Threshold**    |                                                                                                                                       Specify the number of errors that BizTalk Server can encounter before the location is disabled.<br /><br /> **Default value:** 10                                                                                                                                        |
   |      **File Mask**       |                                                                                                                                                                          Specify the file mask filter to use when transmitting files.                                                                                                                                                                          |
   |        **Folder**        |                                                                                                                                                                                Specify the polling location on the FTP server.                                                                                                                                                                                 |
   |   **FTP Server Type**    | New starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br/><br/>Use this property to choose an FTP server that does not require the SYST command. Options are None, AIX, Detect, GXS, MVS, OS400, and Other. <br/><br/>If set to **None**, the SYST command is used. **Other** is used when the OS type does not fit into any of the specified categories. <br /><br /> **Default value:** None |
   |         **Log**          |                                                                                                                                Specify the location to save a copy of the log file. You use this file to diagnose error conditions when sending or receiving files through FTP.                                                                                                                                |
   |    **Max File Size**     |                                                                                                                             Specify the maximum downloadable file size, in megabytes.<br /><br /> Zero (0) indicates no limit on the file size.<br /><br /> **Default value:** 100                                                                                                                             |
   |       **Password**       |                                                                                                                                                                             Specify the user password to log on to the FTP server.                                                                                                                                                                             |
   |         **Port**         |                                                                                                                                                                Specify the port address for this FTP server.<br /><br /> **Default value:** 21                                                                                                                                                                 |
   |    **Representation**    |                                                                                                                                             Select how FTP receives the data.<br /><br /> **Valid values:** binary or ASCII<br /><br /> **Default value:** binary                                                                                                                                              |
   |        **Server**        |                                                                                                                                 Specify the server name or IP address of the FTP server. **Note:**  The URI for a send port or receive location cannot exceed 256 characters.                                                                                                                                  |
   |    **SSO Affiliate**     |                                                                                                                                                                          Specify the Enterprise Single Sign-On affiliate application.                                                                                                                                                                          |
   | **Use name list (NLST)** |                                                                                                                          Specify how the adapter lists files. To view file names instead of the system-defined file listing, set this value to Yes.<br /><br /> **Default value:** No                                                                                                                          |
   |      **User Name**       |                                                                                                                                                                               Specify the user name to log on to the FTP server.                                                                                                                                                                               |

   **Polling**

   |Use this|To do this|  
   |--------------|----------------|         
   |**Delete After Download**|Specify whether the adapter deletes a file from the FTP server after downloading it.<br /><br /> **Default value:** Yes **Note:**|  
   |**Enable Timestamp Comparison**|Specify whether the adapter downloads a file again based on its modified timestamp. In cases when the adapter does not have delete permissions on the FTP server, the MDTM (Modification Time) command allows the adapter to know whether a file has been modified since last download.  Based on the value of this property, the file is downloaded again.<br /><br /> **Default value:** No **Note**:  In case the FTP server does not support MDTM, set the **Redownload Interval** property. **Note:**  This property is applicable only when **Delete After Download** is set to No.|  
   |**Interval**|Specify the interval number for polling this location. To poll continuously, set this value to zero (0).<br /><br /> **Default value:** 60|  
   |**Redownload Interval**|Specify the interval after which the adapter downloads files again. This property is applicable only when both **Delete After Download** and **Enable Timestamp Comparison** are set to No.<br /><br /> **Default value:** -1<br /><br /> -1 indicates that the adapter will not download files again.<br /><br /> 0 indicates that the adapter will download the file in each polling cycle.|  
   |**Unit**|Specify the type of units for the **Interval** and **Redownload Interval** properties.<br /><br /> **Valid values:** Seconds, Minutes, Hours, and Days<br /><br /> **Default value:** Seconds|  

   **SSL**

   |Use this|To do this|  
   |--------------|----------------|
   |**Client Certificate Hash**|Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.<br /><br /> Based on this hash, the client certificate is picked up from the personal store of the user account under which the BizTalk host instance is running.|  
   |**FTPS Connection Mode**|Specify the mode of SSL connection made to the FTPS server.<br /><br /> **Valid Values:** Implicit or Explicit<br /><br /> **Default Value:** Explicit|  
   |**Use Data Protection**|Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Specify this as No for the adapter to send and receive data files as plaintext. **Note:**  This property is applicable only if the **Use SSL** property is set to Yes. <br /><br /> **Valid Values:** Yes or No<br /><br /> **Default Value:** Yes|  
   |**Use SSL**|Specify whether the FTP adapter must use SSL to communicate with the FTPS server.<br /><br /> **Valid Values:** Yes or No<br /><br /> **Default Value:** No|  

   **Tuning Parameters**


   |         Use this         |                                                                                                   To do this                                                                                                   |
   |--------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Receive Data Timeout** | Specify the time in milliseconds before the receive call will abort. You use this property to prevent a slow server from causing the receive location to stop responding.<br /><br /> **Default value:** 90000 |
   |   **Temporary Folder**   |                                               Specify the location for a temporary folder. You use this location to guarantee recovery from a transfer failure.                                                |


6. Click **OK** to save settings.  

7. In the **Receive Location Properties** dialog box, enter the appropriate values to complete the configuration of the receive location and then click **OK** to save settings. For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  

> [!NOTE]
>  Do not configure multiple FTP receive locations to poll the same FTP URL. If multiple FTP receive locations are polling the same URL concurrently then each receive location can receive a copy of the file, which can cause data duplication. This behavior occurs because the FTP protocol has no provision for locking files when reading them from the target URL.  
>   
>  To provide high availability for the FTP receive adapter, you should configure the FTP receive adapter to run in a clustered BizTalk Host instance. See [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).  

## Configure the send port

You can set FTP send port adapter properties in the BizTalk Server Administration console. If properties are not set for the send port, the default send handler values in the BizTalk Server Administration console are used.  

1. In the BizTalk Server Administration console, create a new send port or double-click an existing send port to modify it. See [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options, and in the **Transport** section of the **General** page, specify **FTP** for the **Type** option.  

2. On the **General** page, in the **Transport** section, click the **Configure** button next to **Type**.  

3. In **FTP Transport Properties**, do the following:  

   **Firewall**

   |Use this|To do this|  
   |--------------|----------------|    
   |**Address**|Specify the address of the firewall, either a DNS name or an IP address.|  
   |**Mode**|Select the mode in which the adapter connects to the FTP server.<br /><br /> **Valid values:** Passive and Active<br /><br /> In active mode, the FTP server connects to a port opened by the FTP adapter. In passive mode, the FTP adapter connects to a port opened by the FTP server.<br /><br /> **Default value:** Active|  
   |**Password**|Specify the password for the firewall.|  
   |**Port**|Specify the port for the firewall.<br /><br /> **Valid values:** 1 through 65535 inclusively<br /><br /> **Default value:** 21|  
   |**Type**|Select the type of firewall deployed.<br /><br /> **Valid values:** Socks 4, Socks 5, None<br /><br /> **Default value:** None|  
   |**User**|Specify the user name for the firewall.|  

   **FTP**


   |       Use this       |                                                                                                                                                                                                   To do this                                                                                                                                                                                                   |
   |----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |     **Account**      |                                                                                                                                                 Optional. Specify the account name for the FTP server. This option is and use of this property is discouraged.                                                                                                                                                 |
   |    **After Put**     |                                                                                                                                                          Specify the FTP commands to run after the file PUT. Separate commands with a semicolon (;).                                                                                                                                                           |
   | **Allocate Storage** |                                                                                                       Specify whether to allocate storage space for legacy host systems. This option is provided for backward compatibility.<br /><br /> **Valid values:** No and Yes<br /><br /> **Default value:** No                                                                                                        |
   |    **Before Put**    |                                                                              Specify the FTP commands to run before the file PUT, such as commands to change default values on the FTP server. Separate commands with a semicolon (;). No open command is required. **Note:**  QUIT command is not supported before the file PUT.                                                                              |
   |      **Folder**      |                                                                                                                                                                          Specify the location to move the files to on the FTP server.                                                                                                                                                                          |
   | **FTP Server Type**  | New starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. <br/><br/>Use this property to choose an FTP server that does not require the SYST command. Options are None, AIX, Detect, GXS, MVS, OS400, and Other. <br/><br/>If set to **None**, the SYST command is used. **Other** is used when the OS type does not fit into any of the specified categories. <br /><br /> **Default value:** None |
   |       **Log**        |                                                                                                                               Specify the location to save a copy of a log file. Use this file to diagnose error conditions when sending or receiving files through FTP adapter.                                                                                                                               |
   |     **Password**     |                                                                                                                                                                               Specify the password to log on to the FTP server.                                                                                                                                                                                |
   |       **Port**       |                                                                                                                                                                 Specify the port address for the FTP server.<br /><br /> **Default value:** 21                                                                                                                                                                 |
   |  **Representation**  |                                                                                                                            Select how FTP adapter sends the data, either as binary or as ASCII.<br /><br /> **Valid values:** binary or ASCII<br /><br /> **Default value:** binary                                                                                                                            |
   |      **Server**      |                                                                                                                                                                            Specify the server name or IP address of the FTP server.                                                                                                                                                                            |
   |  **SSO Affiliate**   |                                                                                                                                                                          Specify the Enterprise Single Sign-On affiliate application.                                                                                                                                                                          |
   | **Target File Name** |                                                                                                                   Specify an alternative name for the file. Retaining the default name guarantees unique message names for each message sent.<br /><br /> **Default value:** %MessageID%.xml                                                                                                                   |
   |    **User Name**     |                                                                                                                                                                               Specify the user name to log on to the FTP server.                                                                                                                                                                               |

   **SSL**

   |Use this|To do this|  
   |--------------|----------------|
   |**Client Certificate Hash**|Specify the SHA1 hash of the client certificate that must be used in the Secure Sockets Layer (SSL) negotiation.<br /><br /> Based on this hash, the client certificate is picked up from the personal store of the user account under which the BizTalk host instance is running.|  
   |**FTPS Connection Mode**|Specify the mode of SSL connection made to the FTPS server.<br /><br /> **Valid values:** Implicit or Explicit<br /><br /> **Default value:** Explicit|  
   |**Use Data Protection**|Specify this as Yes if the adapter must use SSL encryption when it sends and receives data files from the FTPS server. Specify this as No for the adapter to send and receive data files as plaintext. **Note:**  This property is applicable only if the **Use SSL** property is set to Yes. <br /><br /> **Valid values:** Yes or No<br /><br /> **Default value:** Yes|  
   |**Use SSL**|Specify whether the FTP adapter must use SSL to communicate with the FTPS server.<br /><br /> **Valid values:** Yes or No<br /><br /> **Default value:** No|  

   **Tuning Parameters**


   |       Use this       |                                                                                                                                                                                                                      To do this                                                                                                                                                                                                                       |
   |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Connection Limit** | Specify the maximum number of concurrent FTP connections that can be opened to the server. A value of 0 means no limit.<br /><br /> **Default value:** 0 **Note:**  This property replaces the registry entry that was used in earlier versions of BizTalk Server to govern the connection limit. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ignores the registry entry used to control the connection limit. |
   | **Temporary Folder** |      Specify the location for a temporary folder on the FTP server. The file is first uploaded here and then moved to the destination FTP folder. In case of transfer failure, the adapter restarts the file upload in ASCII mode of transfer and resumes in binary mode of transfer. **Note:**  If the file transfer is atomic between the temporary location and the relevant location on the FTP server, then the file upload is also atomic.      |


4. Click **OK** and **OK** again to save settings.   


## FTP commands required by the FTP adapter  
The FTP adapter is subject to the limitations of the FTP protocol, and requires that certain FTP commands are available on the source or destination FTP Server.  

The FTP adapter operates as an FTP client and may require that the following commands are available on the FTP server to function correctly: 


| Command  |                                 Required by Receive                                  |                                  Required by Send                                   |
|----------|--------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
|   SYST   | ✔ <br/><br/>Optional starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] | ✔<br/><br/>Optional starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] |
|  STORE   |                                                                                      |                                          ✔                                          |
|   RETR   |                                          ✔                                           |                                                                                     |
|   USER   |                                          ✔                                           |                                          ✔                                          |
|   PASS   |                                          ✔                                           |                                          ✔                                          |
|   CWD    |                                          ✔                                           |                                          ✔                                          |
|   QUIT   |                                          ✔                                           |                                          ✔                                          |
|   PORT   |                                          ✔                                           |                                          ✔                                          |
|   PASV   |                                          ✔                                           |                                          ✔                                          |
|   ABOR   |                                          ✔                                           |                                          ✔                                          |
|   TYPE   |                                          ✔                                           |                                          ✔                                          |
|   RNFR   |                                          ✔                                           |                                          ✔                                          |
|   RNTO   |                                          ✔                                           |                                          ✔                                          |
|   DELE   |                                          ✔                                           |                                          ✔                                          |
|   PWD    |                                          ✔                                           |                                          ✔                                          |
|   LIST   |                                          ✔                                           |                                          ✔                                          |
|   NLST   |                                          ✔                                           |                                          ✔                                          |
|   NOOP   |                                          ✔                                           |                                          ✔                                          |
|   APPE   |                                                                                      |                                          ✔                                          |
|   ALLO   |                                          ✔                                           |                                          ✔                                          |
|   MDTM   |                                          ✔                                           |                                                                                     |
| AUTH TLS |                                          ✔                                           |                                          ✔                                          |
|   PBSZ   |                                          ✔                                           |                                          ✔                                          |
|   PROT   |                                          ✔                                           |                                          ✔                                          |

 For more information about these FTP commands, see:  

-   [RFC 959 - File Transfer Protocol](http://go.microsoft.com/fwlink/p/?LinkId=119603) (http://go.microsoft.com/fwlink/p/?LinkId=119603)  

-   [RFC 4217 - Securing FTP with TLS](http://go.microsoft.com/fwlink/p/?LinkId=183154) (http://go.microsoft.com/fwlink/p/?LinkId=183154)  

-   [RFC 3659 - Extensions to FTP](http://go.microsoft.com/fwlink/p/?LinkId=183155) (http://go.microsoft.com/fwlink/p/?LinkId=183155)  

## Configuring an FTP Adapter to Work with Legacy Hosts

This sections addresses what you need to know to facilitate communication between the FTP adapter and a mainframe computer.   
> [!NOTE]
>  You cannot use the temporary folder function when sending files to an MVS or AS400 host. Input into this field is not supported and will cause errors.  

> [!IMPORTANT]
>  The following information is provided as a guide and should not be substituted for information found in AS400 or IBM documentation.  

## MVS  
 To send files to an FTP server on a mainframe, the mainframe must support IBM Generation Data Group (GDG). In the name field, each file name will append a (+1) to the destination file name (a full path with quotes around it).  

## AS400  
 There are three methods of naming files and defining their paths when transferring files to and from an AS400 system:  

-   **Filename field**: When sending a file to an FTP server, enter the file name in the **Filename** field. The file name must conform to the file-naming conventions of the AS400 system because the file will be stored in the Library File System.  

-   **Quote command**: Use the Quote command to run a script on the remote computer. Enter the Quote command into the **Before GET**, **Before PUT**, **After GET**, and **After PUT** fields on any of the endpoints. Enter the Quote command in the following format:  

    ```  
    QUOTE RCMD <command to be run on the remote system>.  
    ```  

-   **Integrated File System (IFS)**: IFS is an area on the AS400 system that allows the storage of PC-based files and therefore the same naming conventions as a PC. To use the IFS instead of the default Library File System, the first command to enter is `quote site namefmt 1`. This command tells the AS400 system to use the IFS naming convention.    


## More good stuff

[FTP Adapter Property Schema and Properties](../core/ftp-adapter-property-schema-and-properties.md)  

[Best practices and recommendations for the FTP adapter](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)  

[FTP Adapter](../core/ftp-adapter.md)