---
redirect_url: /biztalk/core/creating-peoplesoft-send-handlers/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 
# Optimize configuration
This section contains information about how to optimize your configuration of BizTalk Adapter for PeopleSoft Enterprise and includes parameter descriptions for setting up the adapter.  
  
## Message Overload Protection  
 The `Max Concurrent Calls` parameter is a feature that enables you to optimize your configuration. You use this parameter in instances where the throughput exceeds back-end processing capabilities. You can add the parameter to the adapters in the **Send Port Transport Properties** dialog box to activate message overload protection. The default is -1, meaning the calls are unlimited.  
  
 When BizTalk Server submits messages to the transmit adapter, it first receives a batch from the adapter and invokes `TransmitMessage()` on the batch to transmit each message. When done, BizTalk Server invokes `Done()` on the batch, and the adapter starts transmitting the messages to the back-end. If BizTalk Server obtains multiple batches before `Done` is invoked, the `Done` command might never occur. By setting the maximum number of messages in a batch, you can control messages to the back-end. Changing this parameter takes effect in a minute. BizTalk Server must retrieve the changes to the adapter configuration that is saved in the SQL database.  
  
## Change the Max Concurrent Calls parameter  
  
1.  In the **Send Port Transport Properties** dialog box, enter a **Connection** value.  
  
     The default value is 40 sessions. If you use a smaller value, you might experience degradation in run-time performance. The opposite is also true; a bigger value could exceed the ability of the server and result in run-time errors.  
  
2.  Select **Yes** for **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.  
  
     For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.  
  
     The **Refresh Agent** parameter refreshes both the browsing and the run-time agents. The runtimeagent.exe updates after a delay of one minute or at the next send call.  
  
3.  Provide credentials to access the PeopleSoft system.  
  
     You can use two methods to access the system:  
  
    -   Login Credentials (Transport Properties Login parameters)  
  
    -   Single Sign-On  
  
4.  Select **Yes** for **Use SSO** to use Single Sign-On.  
  
    > [!NOTE]
    >  For more information, see [Secure the adapter](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md). 
  
5.  Select an affiliate application in the list.  
  
     An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as PeopleSoft. Microsoft BizTalk Adapter for PeopleSoft Enterprise uses the credentials of an application user. These credentials are retrieved from the SSO database for the server system for a specified affiliate application. The credentials are those of the user (the application user) who launched the BizTalk project.  
  
    > [!NOTE]
    >  For more information about how to create affiliate applications, see [Creating Affiliate Applications](../core/creating-affiliate-applications2.md), or the Microsoft BizTalk Server online Help.  
  
6.  After providing all required information to accept the connection information, click **Apply**, and then click **OK**.  
  
     You must set connection parameters for the BizTalk Adapter for PeopleSoft Enterprise to access PeopleSoft.  
  
## See Also  
 [Creating PeopleSoft Send Handlers](../core/creating-peoplesoft-send-handlers.md)