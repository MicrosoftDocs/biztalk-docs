---
title: "Host-Initiated Processing2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04a42eb9-2e45-4cfd-9d89-c517a716d124
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Host-Initiated Processing
Host-initiated processing (HIP) enables a host application to call a method of a COM or .NET object, pass parameters to the method, and receive parameters back from the method. As data travels first from the host to the client and then from the client to the host, the data is transformed from a format understandable by the host to the format appropriate for the client  
  
 Host-initiated processing is implemented in the following steps:  
  
1.  The HIP service process, called an application, begins listening for incoming connections on a list of endpoints specified by a local environment definition.  
  
2.  The client application, running on the host, initiates a TCP connection to a HIP system using one of the endpoints  
  
3.  The HIP service process checks if there is an established association between the endpoint and the clients host name or IP address. If no association is found, the connection is aborted.  
  
4.  The association uniquely identifies the work plan that is a sequence of workflows to be performed to complete the clients request. There are three types of work plans:  
  
    1.  Endpoint  
  
    2.  Transaction Request Message  
  
    3.  Data.  
  
## Endpoint  
 The endpoint work plan consists of a single final workflow. The association is directly mapped to a method of a COM object that is to be invoked for the clients request processing. The endpoint workflow performs the following:  
  
1.  Receives client data  
  
2.  Unpacks data and populates parameters for the method  
  
3.  Creates the object and calls the method  
  
4.  Packs returned parameters into the client data  
  
5.  Sends client data  
  
6.  Closes connection.  
  
## Transaction Request Message  
 The Transaction Request Message (TRM) work plan consists of two workflows: TRM and Final workflow. TRM workflow handles initial part of the conversation when client sends the TRM and the workflow replies with the TRM Reply. Depending on the type of TRM, the TRM workflow can use one of three TRM Handlers: Microsoft Concurrent Server, Microsoft Link, IBM Concurrent Server. The TRM workflow performs the following:  
  
1.  Receives and unpacks the TRM using the assigned input format  
  
2.  Passes the TRM to the assigned handler  
  
3.  The handler returns the resolution information and the positive TRM Reply  
  
4.  The resolution information, which is expected to be character data, is converted to Unicode using the code page associated with the host environment  
  
5.  Workflow queries the database if there is a mapping to a method of an object defined for the resolution information  
  
6.  In case the match is not found, the handler is called to get the negative TRM Reply  
  
7.  The TRM Reply is packed using the assigned output format and sent. In the negative case, the connection is aborted  
  
8.  Workflow passes control to Final workflow along with the method identity found  
  
## Data  
 The Data determinant work plan consists of two workflows: Data Determinant and Final workflow. Data Determinant workflow preprocesses the client data trying to find a match to one of the determinants defined for the association. Determinant includes a string of characters and the position of the string in the client data. Each determinant is mapped to a method of an object. At startup the determinants are pre-converted to all code pages of hosts associated with determinants. The rules are enforced that determinants for an end point – host association are not duplicated or one determinant is not a part of the other. The workflow follows these steps:  
  
1.  The list of determinants for the given End Point – Host combination is obtained and sorted by the sum of the length and position in ascending order  
  
2.  The first determinant is taken from the list  
  
3.  A part of client data is received  
  
4.  The data is checked if it matches the determinant  
  
5.  In case of no match the next determinant is taken from the list, more client data received if needed, data compared to determinant  
  
6.  When no available determinant matches the data the connection is aborted  
  
7.  If a determinant is found the control is passed to Final workflow along with the method identity and the client data already read. There could be a situation when the determinant data is located within or even after the client data mapped to the methods parameters.  
  
> [!NOTE]
>  A HIP MVS client must perform a socket shutdown immediately after a socket send and before a socket receive. Failure to perform an immediate socket shutdown causes the TI runtime to refuse the data, break the connection, and log an 808 event message (**A Transaction Integrator HIP application received more data than expected.**) to the server application event log. In addition, the packet containing the data being sent to the workstation might appear misleading: the Microsoft Network Monitor shows the data within the packet and data length not being excessive.  
  
## See Also  
 [Windows-Initiated Processing](../core/windows-initiated-processing2.md)   
 [Programming Models](../core/programming-models2.md)