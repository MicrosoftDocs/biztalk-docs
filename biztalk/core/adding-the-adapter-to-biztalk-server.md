---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: TRUE

ROBOTS: NOINDEX
--- 

# Adding the Adapter to BizTalk Server
Microsoft BizTalk Adapter for JD Edwards OneWorld contains both the Receive Handler and Send Handler folders. The Send Handler folder contains BizTalkServerApplication. BizTalk Adapter for JD Edwards OneWorld is creatable; it runs in-process with BizTalk Server and does not run in an isolated host process.  
  
 Use the following procedure to add the adapter to BizTalk Server.  
  
### To add BizTalk Adapter for JD Edwards OneWorld  
  
1. On the **Start** menu, point to **Program Files**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration** to start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.  
  
2. Expand **BizTalk Server Administration**, expand **BizTalk Group**, and then expand **Platform Settings**.  
  
3. Right-click **Adapters**, point to **New**, and click **Adapter**.  
  
4. In the **Adapter Properties** dialog box, type a name for the adapter. For example, JDEdwards.  
  
5. Select **JDEOneWorld** from the **Adapter** list, and then click **OK**.  
  
## Verifying the Adapter  
 In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, you can verify that the adapter is functioning correctly by looking at the **Logical System** window. On initial installation, this window is empty because you have not yet established a connection to the server system, nor have you created any logical systems.  
  
#### To verify that the adapter is running correctly  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, expand **Platform Settings**, expand **Adapters**, and then select **JDEOneWorld**.  
  
2. In the details pane, right-click **BizTalkServerApplication**, and select **Properties**.  
  
3. Click the **Properties** tab.  
  
4. Set the SQL Connection parameters.  
  
   -   **Define SQL Database Parameters -** The SQL Server Name and Database are those you set at installation. This is the text area that you can redefine the server and database for this adapter.  
  
5. Click **Close** to exit the **Logical System** window.  
  
    Your next step is to add a logical system using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## See Also  
 [Planning and Architecture](../core/planning-and-architecture17.md)   
 [Security in BizTalk Adapter for JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [Adding BizTalk Adapter for JD Edwards OneWorld](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)