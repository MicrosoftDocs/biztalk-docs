---
title: "How to Initialize a Session Integrator Session for LU01 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5a9de5b-a46e-41d5-86da-f2336a2cdb28
caps.latest.revision: 3
---
# How to Initialize a Session Integrator Session for LU0
The first action you must perform when you connect to an LU0 session for Session  Integrator is to create and initialize the <xref:Microsoft.HostIntegration.SNA.Session.SessionLU0> object. As the name implies, <xref:Microsoft.HostIntegration.SNA.Session.SessionLU0> represents the LU0 session to your application, and is the primary interface that you will use to access the SNA network.  
  
 After you initialize the connection, you can begin to send and receive information over the LU0 session.  
  
### To initialize a Session Integrator session for LU0  
  
1.  Determine what type of session you will connect to.  
  
2.  If necessary, create a new session connection by using <xref:Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0>.  
  
     You can create the <xref:Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0> directly if you have all the relevant information. However, you do not need to perform this step. More likely, you will just pass in the LU connection string in step 3.  
  
3.  Create a new session by using <xref:Microsoft.HostIntegration.SNA.Session.SessionLU0>.  
  
4.  Pass the connection information to <xref:Microsoft.HostIntegration.SNA.Session.SessionLU0.Connect%2A>.  
  
     `Connect` contains several overloads: you can choose to connect with an already-created <xref:Microsoft.HostIntegration.SNA.Session.SessionConnection> object, a <xref:Microsoft.HostIntegration.SNA.Session.SessionConnection> object and additional initialization information, or with a connection string and initialization information.  
  
     If you choose to call <xref:Microsoft.HostIntegration.SNA.Session.SessionLU0.Connect%2A> with a connection string, Session Integrator creates a new <xref:Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0> for you. You can directly access the <xref:Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0> object through <xref:Microsoft.HostIntegration.SNA.Session.SessionLU0.Connection%2A>.  
  
5.  If necessary, confirm that you connected by using <xref:Microsoft.HostIntegration.SNA.Session.SessionLU0.IsConnected%2A>.  
  
## Example  
 The following code example demonstrates how to create a session, using a connection string received from the user.  
  
```  
private void CreateSession_Click(object sender, EventArgs e)  
 {  
   try  
     {  
      LUName.Text = LUName.Text.Trim();  
      if (LUName.Text.Length == 0)  
       {  
       MessageBox.Show("You must fill out the LU or Pool Name");  
       return;  
       }  
    _session = new SessionLU0();    _session.Connect("LogicalUnitName=" + LUName.Text, SessionLU0InitType.SSCP);  
                // Receive the logon screen.  
    SessionLU0Data receivedData = _session.Receive(20000, true);  
                // Trace out the received data.  
    TraceData(false, receivedData.Data, receivedData.Indication);  
                // Disable every button and text box.  
    DisableEverything();  
                // Insert User/Password.  
    EnableInsertUserId();  
   }  
catch (Exception ex)  
 {  
  MessageBox.Show(ex.Message);  
 }  
}  
```  
  
 Note that the primary purpose of this code example is to create a new session and connect to the LU using a connection string. However, the example also receives data back over the LU0 session. The example also sends password information using the `EnableInsertUserId` function.  
  
## See Also  
 <xref:Microsoft.HostIntegration.SNA.Session>   
 [Sending a Message with Transaction Integrator for LU0](../core/sending-a-message-with-transaction-integrator-for-lu0.md)   
 [Session Integrator for LU0](../core/session-integrator-for-lu0.md)   
 [Session Integrator for LU0 Code Example](../core/session-integrator-for-lu0-code-example.md)   
 [IcomLU0 Interface](../Topic/IcomLU0%20Interface1.md)