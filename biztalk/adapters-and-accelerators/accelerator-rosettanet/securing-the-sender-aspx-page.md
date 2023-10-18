---
description: "Learn more about: Securing the Sender ASPX Page"
title: "Securing the Sender ASPX Page"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Securing the Sender ASPX Page
This topic describes how to protect the RNIFSend.aspx page from unauthorized use. There are two procedures that you can use:  
  
-   In Internet Information Services (IIS) Manager, secure RNIFSend.aspx to make sure that no unauthorized server will use the RNIFSend.aspx page to transmit unauthorized messages from your network.  
  
-   Use Microsoft Internet Security and Acceleration (ISA) Server to create a protocol rule of outgoing HTTP requests.  
  
### To secure RNIFSend.aspx  
  
1.  On the Web server you use for RNIF message transmission, click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.  
  
2.  In IIS Manager, expand the local computer node, expand **Web Sites**, and then expand **Default Web Site**.  
  
3.  Click **BTARNApp**, and then in the right pane, right-click **RNIFSend.aspx**.  
  
4.  Click **Properties**. On the **File Security** tab, in the **IP address and domain name restrictions** section, click **Edit**.  
  
5.  In the IP Address and Domain Name Restrictions dialog box, click **Denied Access**, and then click **Add**.  
  
6.  In the **Grant Access** dialog box, add all BizTalk Servers performing send operations. If adding a single server, click **Single computer**. In the **IP Address** box, type the IP address for the computer, and then click **OK**.  
  
7.  If adding a group of servers, click **Group of Computers**, and then do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Network ID**|Type the network you want to use.|  
    |**Subnet mask**|Type the subnet mask you want to use.|  
  
8.  Click **OK**.  
  
    > [!NOTE]
    >  If you have separated all your send operations to a separate host running on a separate instance, then you only have to add this computer. You can deny all others access.  
  
9. Click **OK**, and then click **OK** again.  
  
### To create a protocol rule of outgoing HTTP requests  
  
1.  In ISA Management, click **Access Policy**, and then click **Protocol Rules**.  
  
2.  Create a new protocol rule named **HTTP** that uses TCP protocol.  
  
3.  In the property page of your new HTTP protocol rule, in the **Applies To** tab, select **Applies to Client address sets specified below**. Enter only those client IPs that you want to access the page.  
  
## See Also  
 [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md)
