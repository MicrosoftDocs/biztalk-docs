---
title: "Receiving Messages with Transaction Integrator for LU02 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33d57289-c7c2-4d5e-aae2-b6d8a6d10e2a
caps.latest.revision: 3
---
# Receiving Messages with Transaction Integrator for LU0
After you create and initialize your connection, you can receive information from the specified logical unit (LU). The primary way of receiving information with Session Integrator is with the `SessionLU0.Receive` method.  
  
 After sending and receiving messages, you must disconnect from your Session Integrator session.  
  
### To receive information using Session Integrator for LU0  
  
1.  Use SessionLU0.Receive and `SessionLU0data` to wait for data from the LU.  
  
     `Receive` allows you to pass the maximum length of time to wait for information, as well as whether you want to send an automatic acknowledgement. `Receive` returns a `SessionLU0Data` object.  
  
## Example  
 The following code example demonstrates how to receive information with Session Integrator for LU0.  
  
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
    SessionLU0Data receivedData = _session.Receive(20000, true);                // Trace out the received data.  
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
  
 For more information about the code sample, see [Session Integrator for LU0 Code Example](../HIS2010/session-integrator-for-lu0-code-example1.md).  
  
## See Also  
 <xref:Microsoft.HostIntegration.SNA.Session>   
 [How to Terminate a Connection with Session Integrator for LU0](../HIS2010/how-to-terminate-a-connection-with-session-integrator-for-lu01.md)   
 [Session Integrator for LU0](../HIS2010/session-integrator-for-lu01.md)   
 [Session Integrator for LU0 Code Example](../HIS2010/session-integrator-for-lu0-code-example1.md)   
 [IcomLU0 Interface](../HIS2010/icomlu0-interface1.md)