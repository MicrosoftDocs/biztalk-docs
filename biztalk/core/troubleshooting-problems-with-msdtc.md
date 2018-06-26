---
title: "Troubleshooting Problems with MSDTC | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f39cde52-da8f-4cc1-bdc5-e4b828891a79
caps.latest.revision: 36
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Problems with MSDTC
Most BizTalk Server runtime operations require Microsoft Distributed Transaction Coordinator (MSDTC) support to ensure that the operations are transactionally consistent. If MSDTC transaction support is not available, then the associated BizTalk Server runtime operations cannot proceed. The components of BizTalk that are commonly affected when MSDTC transaction support is not configured correctly include (but are not limited to) the Single Sign-On Service, BizTalk host instances, and any SQL Server instances that are connected to by BizTalk Server. This section contains information that describes MSDTC related errors and steps that can be followed to diagnose and resolve problems with MSDTC.  
  
## Errors that can occur if MSDTC transaction support is not configured correctly  
 Errors similar to the following may occur on BizTalk Server when MSDTC transaction support is not configured correctly on the computers in a BizTalk environment:  
  
- "A Microsoft Distributed Transaction Coordinator problem prevented connection to the Configuration database. The transaction manager has disabled its support for remote/network transactions".  
  
- "A Microsoft Distributed Transaction Coordinator problem prevented connection to the Configuration database. The transaction has already been implicitly or explicitly committed or aborted".  
  
- "Error Code: 0x8004d00a, New transaction cannot enlist in the specified transaction coordinator".  
  
- "Could not retrieve transport type data for Receive Location 'MySample ReceiveLocation' from config store. Primary SSO Server 'MyServer' failed. The RPC server is unavailable".  
  
- "Error Code: 0x8004d025, The partner transaction manager has disabled its support for remote/network transactions".  
  
- "Error Code: 0xc0002a24, Could not import a DTC transaction. Please check that MSDTC is configured correctly for remote operation".  
  
- "0x8004d01c  
  
   [0x1705] There was a failure creating the internal work item.  
  
   Make sure that SQL Server is running."  
  
  To resolve MSDTC configuration errors, follow the steps below.  
  
## Ensure NetBIOS name resolution between the BizTalk Server and remote servers is successful  
 Successful MSDTC transactions between computers require that the client computer is able to resolve the NetBIOS name of the server computer to the correct IP address and the server computer is able to resolve the NetBIOS name of the client computer to the correct IP address. To verify that NetBIOS name resolution works in both directions (client to server and server to client) follow these steps:  
  
> [!NOTE]
>  The NetBIOS name is also commonly referred to as the **Network** name.  
  
1. Determine the NetBIOS name of each computer:  
  
   1.  Right-click **My Computer** to display the **System Properties** dialog and click the **Computer Name** tab to view the **Full computer name** assigned to the computer.  
  
   2.  The NetBIOS name is the first portion of the name designated as the **Full computer name** so for example if the **Full computer name** is listed as myserver.company.domain.com, then the NetBIOS name of the computer is **myserver**.  
  
2. Determine the IP Address or addresses that are associated with each computer:  
  
   1.  Launch a command prompt on the client computer, type the following command, and then press ENTER:  
  
       ```  
       ipconfig /all  
       ```  
  
   2.  The IP address or addresses associated with the client computer are listed in the command prompt window.  
  
   3.  Launch a command prompt on the server computer, type the following command, and then press ENTER:  
  
       ```  
       ipconfig /all  
       ```  
  
   4.  The IP address or addresses associated with the server computer are listed in the command prompt window.  
  
3. Verify that the NetBIOS name of each computer is resolved to one of the IP addresses associated with the computer:  
  
   1.  Launch a command prompt on the client computer, type the following command, and then press ENTER:  
  
       ```  
       ping <NetBIOS name of server computer>  
       ```  
  
        The results of the ping command should return an IP address associated with the server computer.  
  
   2.  Launch a command prompt on the server computer, type the following command, and then press ENTER:  
  
       ```  
       ping <NetBIOS name of client computer>  
       ```  
  
        The results of the ping command should return an IP address associated with the client computer.  
  
4. Verify that reverse name lookup of the IP address associated with the NetBIOS name on each computer resolves to the correct computer name.  
  
   1.  Launch a command prompt on the client computer, type the following command, and then press ENTER:  
  
       ```  
       ping -a <IP Address associated with client computer NetBIOS name>  
       ```  
  
        The results of the ping command should return a NetBIOS name or fully qualified domain name that corresponds to the NetBIOS name that was used in step 3a. If the name returned does not match or correspond to the NetBIOS name used in step 3a then IP address reverse lookup will fail which can cause MSDTC transactions to fail.  
  
   2.  Launch a command prompt on the server computer, type the following command, and then press ENTER:  
  
       ```  
       ping -a <IP Address associated with server computer NetBIOS name>  
       ```  
  
        The results of the ping command should return a NetBIOS name or fully qualified domain name that corresponds to the NetBIOS name that was used in step 3b. If the name returned does not match or correspond to the NetBIOS name used in step 3b then IP address reverse lookup will fail which can cause MSDTC transactions to fail.  
  
   If NetBIOS name resolution is not successful in either direction or if reverse name lookup fails then make the appropriate entries in the DNS server, NetBIOS name server, HOSTS file, or LMHOSTS file to correct the problem.  
  
> [!NOTE]
>  The method of name resolution used by the computer varies depending on the NetBIOS node type of the computer. For more information about NetBIOS node types, see [NetBIOS Name Resolution](http://go.microsoft.com/fwlink/?LinkId=201638).  
  
## Ensure that a firewall between the BizTalk Server and remote servers is not blocking ports required for RPC dynamic port allocation  
 MSDTC functionality over the network depends upon RPC functionality over the network. RPC functionality through a firewall requires that specific ports are open to accommodate RPC dynamic port allocation. If a firewall is in place between the BizTalk Server and remote servers, follow the steps in [How to configure RPC dynamic port allocation to work with firewalls](http://go.microsoft.com/fwlink/?LinkId=66831) to accommodate RPC dynamic port allocation.  
  
## Set the appropriate MSDTC Security Configuration options  
 Windows provides security enhancements that govern how MSDTC is accessed over a network. By modifying the MSDTC security settings, you control how MSDTC communicates with remote computers over the network. This table lists the recommended values for the options that are available when configuring MSDTC security settings:  
  
|Configuration Option|Default Value|Recommended Value|  
|--------------------------|-------------------|-----------------------|  
|Network DTC Access|Disabled|Enabled|  
|**Client and Administration**|||  
|Allow Remote Clients|Disabled|Disabled|  
|Allow Remote Administration|Disabled|Disabled|  
|**Transaction Manager Communication**|||  
|Allow Inbound|Disabled|Enabled|  
|Allow Outbound|Disabled|Enabled|  
|Mutual Authentication Required|Enabled|Enabled if all remote machines are running Windows Server 2003 SP1 or Windows XP SP2 or higher, and are configured with “Mutual Authentication Required”.|  
|Incoming Caller Authentication Required|Disabled|Enabled if running MSDTC on cluster.|  
|No Authentication Required|Disabled|Enabled if remote machines are pre-Windows Server 2003 SP1 or pre- Windows XP SP2.|  
|Enable TIP|Disabled|Enabled if running the BAM Portal.|  
|Enable XA Transactions|Disabled|Enabled if communicating with an XA based transactional system such as when communicating with IBM WebSphere MQ using the MQSeries adapter.|  
  
 After applying these changes, the MSDTC service will be restarted.  
  
 To access the MSDTC security configuration options follow these steps:  
  
1.  Click **Start**, click **Run**, and type **dcomcnfg** to launch the **Component Services**Management console.  
  
2.  Click to expand **Component Services** and click to expand **Computers**.  
  
3.  Click to expand **My Computer**, click to expand **Distributed Transaction Coordinator**, right-click **Local DTC**, and click **Properties**.  
  
4.  Click the **Security** tab of the **Local DTC Properties** dialog.  
  
> [!NOTE]
>  Depending on the changes that were made, you may need to reboot the computer to enact the changes. If you are still encountering problems after applying changes and restarting the MSDTC service, reboot the computer on which the changes were made to ensure that the changes take effect.  
  
 If either the **Mutual Authentication Required** or the **Incoming Caller Authentication Required** configuration options are enabled then the client(s) computer account must be granted the **Access this computer from the network** user right. If the computer account for a client computer is not granted the **Access this computer from the network** user right, or is included in the **Deny access to this computer from the network** user right, then DTC communication between the client and server computer will fail.  
  
 The default setting is to grant the Everyone group the **Access this computer from the network** user right. Therefore this user right will not need to be changed unless the default setting has been modified. If the **No Authentication Required** configuration option is enabled then the **Access this computer from the network** user right does not apply to the client(s) computer account.  
  
 To change the users or groups that are granted the "Access this computer from the network" user right, follow these steps:  
  
1. Click **Start**, click **Run**, type **Gpedit.msc**, and then click **OK**.  
  
2. Expand the following items in the Local Computer Policy list:  
  
   -   Computer Configuration  
  
   -   Windows Settings  
  
   -   Security Settings  
  
   -   Local Policies  
  
3. Click **User Rights Assignment**.  
  
4. Double-click **Access this computer from the network**, and then click **Add User or Group**.  
  
5. Click **Object Types**, select **Computers** and click **OK**.  
  
6. Add the computer name or the group name in the **Enter the object names to select** area.  
  
7. Click **Check Names** to verify the entry.  
  
8. Click **OK** twice.  
  
   To change the users or groups that are included in the **Deny access to this computer from the network** user right, follow these steps:  
  
9. Expand the following items in the Local Computer Policy list:  
  
   -   Computer Configuration  
  
   -   Windows Settings  
  
   -   Security Settings  
  
   -   Local Policies  
  
10. Click **User Rights Assignment**.  
  
11. Double-click **Deny access this computer from the network**, and then click to select the computer name or group that you want to remove from this user right.  
  
12. Click **Remove** and then click **OK**.  
  
## Set the appropriate values for the EnableAuthEpResolution and RestrictRemoteClients options  
 Windows enhances security by requiring authenticated calls to the RPC interface. This functionality is configurable through the **EnableAuthEpResolution** and **RestrictRemoteClients** registry keys. To ensure that remote computers are able to access the RPC interface, follow these steps:  
  
> [!WARNING]
>  Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system. Use Registry Editor at your own risk. For more information about how to back up, restore, and modify the registry, see the Microsoft Knowledge Base article "Description of the Microsoft Windows registry" at [Description of the Microsoft Windows registry](http://go.microsoft.com/fwlink/?LinkId=62729).  
  
1.  Click **Start**, click **Run**, type **regedit.exe**, and then click **OK** to start Registry Editor.  
  
     Navigate to **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT**  
  
2.  Under the **RPC** key, create the following DWORD entries with the indicated values. If the **RPC** key does not exist then it must be created.  
  
    |DWORD entry|Default value|Recommended value|  
    |-----------------|-------------------|-----------------------|  
    |EnableAuthEpResolution|0 (disabled)|1|  
    |RestrictRemoteClients|1 (enabled)|0|  
  
3.  Close Registry Editor.  
  
4.  Restart the MSDTC Service.  
  
> [!NOTE]
>  Depending on the changes that were made, you may need to reboot the computer to enact the changes. If you are still encountering problems after applying changes and restarting the MSDTC service, reboot the computer on which the changes were made to ensure that the changes take effect.  
  
## If Windows Firewall is running, add an exception for the MSDTC service  
 The Windows Firewall service may block MSDTC communications between computers. To ensure that MSDTC communications are not blocked between computers, add msdtc.exe to the Windows Firewall exception list if the Windows Firewall service is running.  
  
1.  Click **Start**, click **Run**, type **firewall.cpl**, and then click **OK** to display the **Windows Firewall** dialog box.  
  
2.  Click **Allow a program through the Windows Firewall** to display the **Windows Firewall Settings** dialog box.  
  
3.  Click the **Exceptions** tab of the **Windows Firewall Settings** dialog box.  
  
4.  Click **Add Program** to display the **Add a Program** dialog box.  
  
5.  Click **Browse** and navigate to *%system32%*\msdtc.exe.  
  
    > [!NOTE]
    >  Launch a command prompt, type **echo %system32%** and press **Enter** to determine the location of the \System32 directory on this computer.  
  
6.  Click to select **msdtc.exe** and click **Open**.  
  
7.  Click **Change scope** to specify the set of computers for which MSDTC communications should be allowed and click **OK**.  
  
8.  Click **OK** in the **Add a Program** dialog box and click **OK** in the **Windows Firewall Settings** dialog box.  
  
9. Close the **Windows Firewall** dialog box.  
  
10. Stop and restart the Distributed Transaction Coordinator service.  
  
    -   Launch a command prompt, type **net stop msdtc** and press **Enter**.  
  
    -   After the Distributed Transaction Coordinator service has stopped, type **net start msdtc** and press **Enter**.  
  
## Use DTCTester or DTCPing to verify MSDTC functionality over the network  
 Use the DTCTester utility to verify transaction support between two computers if SQL Server is installed on one of the computers. The DTCTester utility uses ODBC to verify transaction support against a SQL Server database. For more information about DTCTester see [How to Use DTCTester Tool](http://go.microsoft.com/fwlink/?LinkId=66232).  
  
 Use DTCPing to verify transaction support between two computers if SQL Server is not installed on either computer. The DTCPing tool must be run on both the client and server computer and is a good alternative to the DTCTester utility when SQL Server is not installed on either computer. For more information about DTCPing, see [How to troubleshoot MS DTC firewall issues](http://go.microsoft.com/fwlink/?LinkId=61915).  
  
> [!IMPORTANT]
>  If DTCPing returns the warning that “WARNING:the CID values for both test machines are the same” then follow the steps in the section **Ensure that MSDTC is assigned a unique CID value** to accommodate proper MSDTC functionality between the test machines.  
  
## Ensure that MSDTC is assigned a unique CID value  
 The MSDTC feature of the Windows operating system requires unique CID values to ensure that MSDTC functionality between computers works correctly. Disk duplicate images of Windows installations must have unique CID values or MSDTC functionality may be impaired. This can occur when using virtual hard disks to deploy an operating system to a virtual machine.  
  
 To determine if MSDTC CID values for computers that are running the Windows operating system are unique, check the values for the entries under the HKEY_CLASSES_ROOT\CID registry key on both computers. If these values are not unique for each computer then follow the steps in the section **Consider reinstalling the Distributed Transaction Coordinator service if other troubleshooting steps are not successful** to reinstall MSDTC on one of the computers, which will then generate unique MSDTC CID values for that computer and accommodate proper MSDTC operations.  
  
## Error “New transaction cannot enlist in the specified transaction coordinator (0x8004d00a)” occurs if the MSDTC connection between a client computer and a server computer is closed  
 In certain scenarios, it is possible that an existing MSDTC connection between a client and server is closed and subsequent attempts to use this connection will result in the following error message:  
New transaction cannot enlist in the specified transaction coordinator (0x8004d00a)  
For more information, see [Error message when you try to start a transaction in MS DTC: "New transaction cannot enlist in the specified transaction coordinator"](http://support.microsoft.com/kb/922430).  
  
## Consider reinstalling the Distributed Transaction Coordinator service if other troubleshooting steps are not successful  
 If other attempts at troubleshooting problems with MSDTC are not successful consider uninstalling and reinstalling MSDTC. Follow these steps to uninstall and reinstall MSDTC:  
  
1.  Open a command prompt as Administrator.  
  
2.  At the command prompt, type the following to uninstall the Distributed Transaction Coordinator service:  
    `msdtc -uninstall`  
  
3.  At the command prompt, type the following to install the Distributed Transaction Coordinator service:  
    `msdtc –install`  
  
> [!IMPORTANT]
>  Reinstalling MSDTC may change the default behavior of the Distributed Transaction Coordinator service. Follow these steps after reinstalling MSDTC to ensure that the Distributed Transaction Coordinator service works correctly:  
> 
> - Reinstalling MSDTC may reset MSDTC Security Configuration options back to default values. Verify that the MSDTC Security Configuration options are set to the appropriate values after reinstalling MSDTC.  
>   -   Reinstalling MSDTC may change the **Startup Type** value for the Distributed Transaction Coordinator service. Verify that the **Startup Type** value for the Distributed Transaction Coordinator service is set to **Automatic** after reinstalling MSDTC.  
>   -   Reinstalling MSDTC may require a reboot of the computer. To ensure that the Distributed Transaction Coordinator service works correctly, reboot the computer after reinstalling MSDTC.  
  
## See Also  
 [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Troubleshooting a Windows Server Cluster](../core/troubleshooting-a-windows-server-cluster.md)