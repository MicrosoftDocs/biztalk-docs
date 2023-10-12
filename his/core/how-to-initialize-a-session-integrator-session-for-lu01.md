---
description: "Learn more about: Initialize a Session Integrator Session for LU0"
title: "Initialize a Session Integrator Session for LU01"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Initialize a Session Integrator Session for LU0
The first action you must perform when you connect to an LU0 session for Session  Integrator is to create and initialize the `Microsoft.HostIntegration.SNA.Session.SessionLU0` object. As the name implies, `Microsoft.HostIntegration.SNA.Session.SessionLU0` represents the LU0 session to your application, and is the primary interface that you will use to access the SNA network.  
  
 After you initialize the connection, you can begin to send and receive information over the LU0 session.  
  
## Initialize a Session Integrator session for LU0  
  
1.  Determine what type of session you will connect to.  
  
2.  If necessary, create a new session connection by using `Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0`.  
  
     You can create the `Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0` directly if you have all the relevant information. However, you do not need to perform this step. More likely, you will just pass in the LU connection string in step 3.  
  
3.  Create a new session by using `Microsoft.HostIntegration.SNA.Session.SessionLU0`.  
  
4.  Pass the connection information to `Microsoft.HostIntegration.SNA.Session.SessionLU0.Connect%2A`.  
  
     `Connect` contains several overloads: you can choose to connect with an already-created `Microsoft.HostIntegration.SNA.Session.SessionConnection` object, a `Microsoft.HostIntegration.SNA.Session.SessionConnection` object and additional initialization information, or with a connection string and initialization information.  
  
     If you choose to call `Microsoft.HostIntegration.SNA.Session.SessionLU0.Connect%2A` with a connection string, Session Integrator creates a new `Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0` for you. You can directly access the `Microsoft.HostIntegration.SNA.Session.SessionConnectionLU0` object through `Microsoft.HostIntegration.SNA.Session.SessionLU0.Connection%2A`.  
  
5.  If necessary, confirm that you connected by using `Microsoft.HostIntegration.SNA.Session.SessionLU0.IsConnected%2A`.  
  
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
 [Sending a Message with Transaction Integrator for LU0](../core/sending-a-message-with-transaction-integrator-for-lu01.md)   
 [Session Integrator for LU0](../core/session-integrator-for-lu02.md)   
 [Session Integrator for LU0 Code Example](../core/session-integrator-for-lu0-code-example2.md)   
 [IcomLU0 Interface](./icomlu0-interface2.md)
