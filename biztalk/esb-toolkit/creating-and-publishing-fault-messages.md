---
description: "Learn more about: Creating and Publishing Fault Messages"
title: "Creating and Publishing Fault Messages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Creating and Publishing Fault Messages
To help you understand how to use the features of the Exception Management Framework to manage exceptions, this section presents a common scenario based on the submission of a message to an ESB application.  
  
 The scenario consists of a user submitting an invoice to the system. During the course of processing the invoice in an orchestration, the BizTalk Business Rules Engine throws an application exception because some part of the data is incorrect. The business process should catch the exception, send the offending message to another person or system that can correct the message, and then resubmit the message for processing.  
  
 When using the ESB Failed Orchestration Exception Routing feature, the process steps are the following:  
  
1.  Code in the exception handler detects the error and creates a fault message by calling the **CreateFaultMessage** method, as shown in the following code example.  
  
    ```csharp  
    // Create fault exception message.  
    faultMsg = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.CreateFaultMessage();  
    ```  
  
2.  The ESB Exception mechanism automatically inserts the error description into the fault message context (for example, "The Business Rules Engine threw a divide by zero error while processing the LoanProcessing policy.").  
  
3.  The ESB Exception mechanism automatically promotes failure-specific properties and application-specific properties into the fault message context and sets the values from the current environment. These properties are the following:  
  
    -   **Application** (auto-populated)  
  
    -   **DateTime** (auto-populated as a UTC value)  
  
    -   **Description** (auto-populated—the exception message)  
  
    -   **ErrorType** (auto-populated—the exception type)  
  
    -   **MachineName** (auto-populated—the current server name)  
  
    -   **Scope** (auto-populated—the Scope shape that contains the current exception handler)  
  
    -   **ServiceName** (auto-populated—the orchestration name)  
  
    -   **ServiceInstanceID**(auto-populated—the orchestration instance ID as a GUID)  
  
4.  Code in the exception handler sets other properties of the fault message as required, as shown in the following code example.  
  
    ```csharp  
    // Set fault message properties.  
    faultMsg.Body.FailureCategory = "MessageBuild";  
    faultMsg.Body.FaultCode = 1000;  
    faultMsg.Body.FaultDescription = "Some error occurred";  
    faultMsg.Body.FaultSeverity =  
       Microsoft.Practices.ESB.ExceptionHandling.FaultSeverity.Severe;  
    ```  
  
5.  The ESB Exception mechanism automatically serializes the current **Exception** object into the fault message.  
  
6.  Optionally, code in the exception handler can add current orchestration messages to the ESB fault message using the **AddMessage(faultMsg, messageToAdd)** method. This method serializes and persists the message, including all the context properties, as shown in the following code example.  
  
    ```csharp  
    // Add other current orchestration messages to the fault message.  
    Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.AddMessage(  
                                faultMsg, approvedRequestMsg);  
    Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.AddMessage(  
                                faultMsg, DeniedRequestMsg, @"c:\temp");  
    ```  
  
7.  Code in the exception handler publishes the ESB fault message to the Message Box database using a direct bound port.  
  
8.  If publishing succeeds, the following events occur:  
  
    -   Orchestration or send port subscriptions can process the ESB fault message and extract any added messages, complete with their context property values.  
  
    -   A global exception handler (a send port) automatically publishes the ESB fault message to the ESB Management Portal.
