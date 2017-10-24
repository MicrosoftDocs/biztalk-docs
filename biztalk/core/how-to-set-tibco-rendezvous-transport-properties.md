---
redirect_url: /biztalk/core/creating-tibco-rendezvous-send-handlers/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# How to Set TIBCO Rendezvous Transport Properties
The TIBCO Rendezvous Transport property is used for run time. In the **Transport Properties** screen, you set the connection parameters that identify the TIBCO Rendezvous domain where you want to publish the generated messages.  
  
## Enter TIBCO Rendezvous Transport properties  
  
1.  On the **TIBCO Rendezvous Transport Properties** screen, expand **Certified Sender Properties** and enter the following information.  
  
     ![](../core/media/sadp-tibcoren-transs.gif "SAdp_TibcoRen_Transs")  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Ledger name**|Default value is blank. Ledger file name to use for persistent certified message delivery. Use local drives only.|  
    |**Reusable name**|Default value is blank. Reusable correspondent name to use for certified message delivery. The name must be unique among all certified message correspondent names on the network.|  
  
2.  Expand **Credentials** and enter the following information for connection to the server.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Password**|Default value is blank. Password for login to a Tibco Rendezvous daemon.|  
    |**User name**|Default value is blank. User name for Tibco Rendezvous daemon.|  
  
3.  Expand **General Settings** and enter the following information for connection to the TIBCO Rendezvous server.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Code Page Number**|Default value is 65001 (code page for UTF-8 encoding). This is the code page that the TIBCO Rendezvous SDK uses for String encoding.|  
    |**Default Subject Name**|Default is empty. The subject name is set in the orchestration. If a port is used for one message type, you can provide a default subject name, and you can simplify orchestrations by removing the need to set the Subject name property.|  
    |**Enable Time Batch**|Default value is False. Enable/Disable TIBCO Rendezvous Time Batch feature.|  
    |**Map Unsupported types to string**|Default value is True. If true, unsupported types are mapped to string if it is possible. If False, a run-time error is generated.|  
    |**Path to Binaries, such as TIBCO Rendezvous assemblies**|Provide this information if it is not already in the PATH environment variable.|  
    |**Preserver Order**|Default value is True. Enables logic to send messages to TIBCO Rendezvous in the same order they were received from BizTalk Server. This parameter forces publishing in the same order; it does not mean that subscribers receive them in the same order.|  
    |**Send Port Identifier**|This identifier appears in log messages associated with this port. It is provided as a convenience.|  
  
4.  Expand **Rendezvous Transport** and enter the information for connection to the TIBCO Rendezvous server, click **Apply**, and then click **OK**.  
  
     You must set connection parameters for Microsoft BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Daemon**|Default is empty.<br /><br /> Rendezvous Transport Daemon parameter.|  
    |**Network**|Default is empty.<br /><br /> Rendezvous Transport Network parameter.|  
    |**Service**|Default is empty.<br /><br /> Rendezvous Transport Service parameter.|  
  
5.  Provide credentials using Single Sign-On (SSO).  
  
     There are two methods that you can use to access the TIBCO Rendezvous system. You can use Credentials (User Name and Password parameters) or Single Sign-On.  
  
    1.  Select **Yes** in the **Use SSO** to use Single Sign-On.  
  
        > [!NOTE]
        >  See [Security](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md) for information about how to set up SSO.  
  
    2.  Select an affiliate application from the list.  
  
         An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as TIBCO Rendezvous. Microsoft BizTalk Adapter for TIBCO Rendezvous uses the credentials of an application user. These credentials are retrieved from the SSO database for the server system for a specified affiliate application.  
  
        > [!NOTE]
        >  For information about how to create an affiliate application, see [Creating Affiliate Applications](../core/creating-affiliate-applications1.md).  
  
6.  Click **Apply**, and then click **OK** after providing all required information to accept the connection information.  
  
     You must set connection parameters for BizTalk Adapter for TIBCO Rendezvous to access TIBCO Rendezvous .  
  
## See Also  
 [Creating TIBCO Rendezvous Send Handlers](../core/creating-tibco-rendezvous-send-handlers.md)