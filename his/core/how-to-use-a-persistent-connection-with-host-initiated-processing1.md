---
description: "Learn more about: How to Use a Persistent Connection with Host-Initiated Processing"
title: "Use a Persistent Connection with Host-Initiated Processing | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba6038f9-bf1f-4090-b4e4-f97bcb4490a0
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Use a Persistent Connection with Host-Initiated Processing
A persistent connection is a connection that stays open past the duration of a specific call. Because your application does not need to re-create the connection on each call, you can use a persistent connection to increase the efficiency of your Host-initiated application. An application that uses a persistent connection with Host-initiated Processing (HIP) operates in many ways the same way as a Windows-Initiated Processing (WIP). The difference, of course, is that the mainframe initiates and terminates the connection, while the windows application responds to the requests of the mainframe.  
  
> [!NOTE]
>  Host Integration Server supports many of the same programming environments for HIP as for WIP. The exceptions are IMS Connect, Distributed Program Call (DPC), and SNALink, which are not supported for HIP persistent connections.  
  
## Use a persistent connection with HIP  
  
1.  Receive a call with your Windows application from the mainframe, indicating that a connection has been created.  
  
     It is the responsibility of the mainframe application to request the persistent connection.  
  
2.  Have your Windows application react to the request in the relevant manner.  
  
     There is nothing specific your application must do in order to use a persistent connection: creating and terminating the connection is the responsibility of the mainframe application.  
  
3.  Optionally, you can create a new instance of the HIPServerUserContext to query the status of the connection.  
  
     The new instance is automatically created with the context information for the relevant connection. Using HIPServerUserConext, you can determine what type of connection the mainframe has created, and react accordingly.  
  
## Example  
 The following code is pulled from the CICS sample application in the SDK. The sample uses the CONNTYPE of the server object to perform different actions.  
  
```  
decimal GetAccountBalance(object[] contextArray)  
        {  
            decimal ReturnBalance = 0.0m;  
            string ConnType;  
            object contextValue;  
  
            _TIServerContext.ReadContext("CONNTYPE", out contextValue, ref contextArray);  
  
            if (contextValue == null)  
                ReturnBalance = 123.45m;  
            else  
            {  
                ConnType = contextValue.ToString();  
                ConnType.ToUpper();  
                switch (ConnType)  
                {  
                    case "OPEN":  
 // Set the initial value of the Account Balance  
 // and save it in a global varaible and return it.  
                        ReturnBalance = 123.45m;  
                        _AccountBalance = ReturnBalance;  
                        break;  
  
                    case "USE":  
 // Increase the value of the global Account Balance  
 // varaible and return its value. Save this new value  
 // in the global variable for later use  
                        _AccountBalance += 100;  
                        ReturnBalance = _AccountBalance;  
                        break;  
  
                    case "CLOSE":  
 // Increase the value of the global Account Balance  
 // variable and return the new value. Set the global variable  
 // to zero because the "CLOSE" call indicates that we are   
 // done with it.  
                        ReturnBalance = _AccountBalance + 150;  
                        _AccountBalance = 0.0m;  
                        break;  
  
                    case "UNKNOWN":  
                    default:  
                        _AccountBalance = 0.0m;  
                        ReturnBalance = 123.45m;  
                        break;  
                }  
            }  
  
            return ReturnBalance;  
        }  
```  
  
 The code sample uses a global variable to store information. It is also possible to use the context object itself to store information. Although not shown here, it is possible to use the context object to pass information back to the windows application.  
  
## See Also  
 [Persistent Connections](../core/persistent-connections2.md)   
