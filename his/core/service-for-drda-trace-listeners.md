---
title: "Service for DRDA Trace Listeners | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6dfc697-aa81-4ee7-b311-b63e702c4bd8
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Service for DRDA Trace Listeners
You can troubleshoot problems with the DRDA Service by understanding looking at trace output, the Windows event log entries, and understanding solutions to common problems.  
  
 The DRDA Service supports multiple concurrent trace listeners, including the default Text Encoder, default Console Encoder, ETW (Event Tracing for Windows) listener, and optional Custom Encoder. The drdaServiceTraceListeners element contains one or more drdaServiceTraceListener elements to instruct the DRDA Server to send trace output to optional custom text trace listeners.  
  
## Trace Format  
 The console, text and custom trace listener output is formatted into five (5) columns of data.  
  
### Type  
 Column 1 is the Type of data. The Type is a string value. The Type column is divided from the Session Identifier column by a colon. The DRDA Server writes a Type value of Information only.  
  
### Session Identifier  
 Column 2 is the Session Identifier. The Session Identifier is an integer value. The Session Identifier column is divided from the Type column by a colon. The Session Identifier can be used as a correlation identifier, matching connection information to command execution information. The DRDA Service writes a Session Identifier of 0 for non-client connections, including service startup information and DRDA Service-to-DRDA Service communications.  
  
 Information:0:0:[Jan 16 2013 16:52:53.815] Microsoft Service for DRDA (build: 9.0.1870.0 )  
  
 Information:0:0:[Jan 16 2013 16:52:53.817] TCP communication manager listening on port 446  
  
### Trace Level  
 Column 3 is the Trace Level. The Trace Level is an integer value. The Trace Level column is divided from the Session Identifier column by a colon. The DRDA Server writes a Trace Level value of 0 to 6, corresponding to the traceLevel attribute value.  
  
### Datetime  
 Column 4 is a Datetime value. The Datetime value is enclosed in square brackets to separate this column from the preceding Trace Level and following Trace Data columns.  
  
### Trace Data  
 Column 5 is the Trace Data value. The Trace Data is a string value.