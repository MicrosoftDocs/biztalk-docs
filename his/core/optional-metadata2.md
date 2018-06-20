---
title: "Optional Metadata2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 473a8667-a6c6-49ac-8dc2-11217575265d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Optional Metadata
As a developer, you can choose to have the Transaction Integrator (TI) run-time environment send and receive metadata to and from the mainframe transaction program (TP), and you can choose the content of that metadata.  
  
> [!NOTE]
>  Metadata is not supported for distributed program call (DPC).  
  
 You can send or receive:  
  
- No metadata.  
  
- Only the method name as metadata.  
  
- All metadata including the method name.  
  
  The TI run-time environment sends or receives metadata to or from the TP as instructed. Metadata assists the TP in:  
  
- Identifying the format of the metadata (version information).  
  
- Identifying the name of the method used to invoke the TP.  
  
- Reporting detailed error information back to the client.  
  
  The metadata is not visible to the Automation client. The metadata is delivered to (or received from) the host TP as part of the request message sent to (or response message received from) the TP.  
  
  The metadata set includes the following data:  
  
- TI run-time version.  
  
   A string of characters, such as "Microsoft TI version 1.0.0," that uniquely identifies the TI run-time environment version that generated the request.  
  
- Method name (32-character string) invoked by the client application code.  
  
- Metadata block ID.  
  
   A GUID, in character format, that uniquely identifies this block of exception data. The GUID supports the ability to have additional exception formats in the future and helps to ensure that any data received is valid.  
  
- Variables with no assigned uses to date (reserved):  
  
  -   Boolean flag indicating whether the TP is ready to commit.  
  
  -   Boolean flag indicating whether the TP is ready to perform additional work.  
  
  -   Two Short Integers to hold pieces of the TI run-time environment version number, one Short Integer to hold the major version number and the other to hold the minor version number.  
  
- Exception Block (used only in replies).  
  
   A GUID, in binary format, that uniquely identifies this block of exception data. The GUID allows support of additional exception formats in the future and helps ensure the data received is valid:  
  
  -   Boolean flag that indicates whether the TP is ready to commit.  
  
  -   Boolean flag that indicates whether the TP is ready to perform additional work.  
  
  -   Boolean flag that indicates whether an exception should be returned to the client application. If set, this flag also causes the transaction to quit.  
  
  -   16-bit integer that identifies the error (see the note later in this topic). You can assign this value, along with the 256-character message that describes the error, from the server so that the assigned value is returned when a TI run-time error occurs.  
  
  -   32-bit integer that identifies the context ID in the TP Help file (if any).  
  
  -   256-character message that describes the error. You can assign this value, along with the 16-bit integer that identifies the error from the server, so that the assigned value is returned when a TI run-time error occurs.  
  
  Metadata is always located at the beginning of the message.  
  
> [!NOTE]
>  TI error messages have numbers in the range from 0 through 9999. Metadata error message numbers returned from the mainframe can fall within the same range. To distinguish TI error messages from metadata messages returned from the mainframe, TI adds 10000 to the number of any metadata error message returned from the mainframe.