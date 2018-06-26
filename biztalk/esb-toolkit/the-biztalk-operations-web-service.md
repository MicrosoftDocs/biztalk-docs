---
title: "The BizTalk Operations Web Service | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af38815f-f643-4598-9148-6499071d12e4
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The BizTalk Operations Web Service
The Microsoft BizTalk Operations Web service exposes information about the objects and messages in BizTalk Server. The service name is **ESB.BizTalkOperationsService**, and the service exposes a wide range of methods that return items such as a list of hosts, orchestrations, applications, and the BizTalk application status.  
  
 The following methods are available:  
  
-   **Applications**. This method takes no parameters, and it returns the name and description of all installed BizTalk applications as a collection of **BTApplication** objects.  
  
-   **ApplicationStatus**. This method takes as a parameter the application name, and it returns information about the specified BizTalk application as a **BTSysStatus** instance. This information includes orchestrations, send ports, receive locations, and host details.  
  
-   **GetLiveMessageBody**. This method takes as parameters a message ID and an instance ID, and it returns the body of that message from the live environment as a **BTMsgBody** instance.  
  
-   **GetMessageInstances**. This method takes as a parameter the message type, and it returns all matching messages as a collection of **BTMsgInstance** objects.  
  
-   **GetOrchestrationInstances**. This method takes as parameters the name of an orchestration, and it returns a collection of **BTOrchestrationInstance** object that contain details of the matching orchestrations.  
  
-   **GetTrackedMessageBody**. This method takes as a parameter a message GUID, and it returns the body of that message as a **BTMsgBody** instance after it is processed in BizTalk.  
  
-   **Hosts**. This method takes as a parameter the name of a host, and it returns information about the specified host instance as a collection of **BTHost** instances. Use an empty string for the host name parameter to return information about all host instances.  
  
-   **MessageFlowTree**. This method takes as a parameter an instance ID, and it returns details of the message flow for that message as a **RouteTreeNode** instance.  
  
-   **Orchestrations**. This method takes as a parameter the name of an orchestration, and it returns all the information for that orchestration as a **BTSysStatus** instance. Use an empty string for the orchestration name parameter to return information about all orchestrations.  
  
-   **ReceiveLocations**. This method takes as a parameter the name of a receive location, and it returns all the information for matching locations as a **BTSysStatus** instance. Use an empty string for the receive locations name parameter to return information about all locations.  
  
-   **ReceiveLocationsByDescription**. This method takes as a parameter the description of a receive location, and it returns all the information for matching locations as a **BTSysStatus** instance. Use an empty string for the description parameter to return information about all locations.  
  
-   **SendPorts**. This method takes as a parameter the name of a send port, and it returns all the information for matching ports as a **BTSysStatus** instance. Use an empty string for the send port name parameter to return information about all ports.  
  
-   **SendPortsByDescription**. This method takes as a parameter the description of a send port, and it returns all the information for matching ports as a **BTSysStatus** instance. Use an empty string for the description parameter to return information about all ports.  
  
-   **StatusChanged**. This method takes as a parameter a timestamp, and it returns details of BizTalk objects (such as ports, hosts, and orchestrations) modified since the specified timestamp as a **BTSysStatus** instance.  
  
-   **SystemStatus**. This method takes no parameters, and it returns full details of the BizTalk system status as a **BTSysStatus** instance.  
  
-   **UpdateReceiveLocationDescription**. This method updates the description of a specified receive location using parameter values that contain the application name, the receive port name, the receive location name, and the receive location description. It returns a String that indicates the result of the operation. Note that the test client application reads this information from its App.config file.  
  
-   **UpdateSendPortDescription**. This method updates the description of a specified send port using parameter values that contain the send port name and the send port description. It returns a String that indicates the result of the operation. Note that the test client application reads this information from its App.config file.  
  
## Configuring the BizTalk Operations Web Service  
 The BizTalk Operations Web service either communicates directly with the BizTalk Server management databases using Windows Management Instrumentation (WMI) or it uses the BizTalk Operations and Explorer API to obtain the information it requires. Therefore, you must make sure that your system meets the following conditions and that you configure the following security permission settings:  
  
- Set the **allowOverride** attribute in the machine-level Web.config file to **false** to make sure developers cannot change the trust level of their applications.  
  
- By default, the BizTalk Operations Web service is not configured to require Secure Sockets Layer (SSL) when accessed by clients. You should configure the service so that it requires SSL for client access, and protect the connection between the Internet Information Services (IIS) Web service host computer and the computer running SQL Server that hosts the BizTalkMgmtDb database using network-level IPSec and appropriate file-level access control list (ACL) permissions.  
  
- Users accessing the BizTalk Operations Web service must be members of the default BizTalk Server Administrators group for some methods and members of the default BizTalk Application Users group for other methods.  
  
- You must make sure that the BizTalk Operations Web service resides in an IIS virtual directory named ESB.BizTalkOperationsService that has anonymous access disabled.  
  
- Users must have **SELECT** permission in SQL Server for several tables located in the BizTalkMgmtDb database and the BizTalkMsgBoxDb database. Use SQL Server Management Studio to set the following permissions:  
  
  -   In the BizTalkMgmtDb database, configure the BTS_ADMIN_USERS database role with **SELECT** permission on the following tables:  
  
      -   adm_Server2HostMapping  
  
      -   adm_Server  
  
      -   adm_hostInstance  
  
  -   In the BizTalkMsgBoxDb database, configure the BTS_ADMIN_USER database role with **SELECT** permission on the ProcessHeartbeats table.  
  
  In SQL Server Management Studio, you can configure the required permissions. To do this, expand **Security** in the left pane tree view of Object Explorer, expand **Roles**, expand **DatabaseRoles**, select the BTS_ADMIN_USERS role, and then edit the properties for this role, as shown in Figure 1.  
  
  ![SQL Server Mgmt Studio](../esb-toolkit/media/ch4-sqlservermgmtstudio.gif "Ch4-SQLServerMgmtStudio")  
  
  **Figure 1**  
  
  **Editing permissions for the BTS_ADMIN_USERS database role in Microsoft SQL Server Management Studio**  
  
> [!NOTE]
>  You must configure this service to use Windows Integrated Security and run under the built-in NETWORK SERVICE account. You must also enable Kerberos authentication on your IIS Web server so that it sends the header **Negotiate,NTLM** to the client. For more information, see [How to configure IIS to support both the Kerberos protocol and the NTLM protocol for network authentication](http://go.microsoft.com/fwlink/?LinkId=186430)([http://go.microsoft.com/fwlink/?LinkId=186430](http://go.microsoft.com/fwlink/?LinkId=186430)).  
>   
>  By default, the BizTalk Operations Web service is not configured to require SSL when accessed by clients. You should configure the service so that it requires SSL for client access and protect the connection between the IIS Web service host computer and the server that hosts the UDDI service using network-level IPSec and appropriate file-level ACL permissions.