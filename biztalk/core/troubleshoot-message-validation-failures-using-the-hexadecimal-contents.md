---
title: "Troubleshooting Message Validation Failures by Viewing the Hexadecimal Contents of Suspended Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cf14cd9-2d4b-43a3-9738-52bfd879e1e4
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Message Validation Failures by Viewing the Hexadecimal Contents of Suspended Messages
If a message is suspended due to validation failures, it may be helpful to view the hexadecimal representation of the message parts to determine the cause of the validation failure. This topic lists steps that can be followed to view the hexadecimal representation of the parts of a suspended message.

## Use the Message Details dialog box to view message parts
 Follow these steps to view the hexadecimal representation of message parts:

1.  Use the **Query** tab in the BizTalk Administration Console to return a result set with one or more suspended messages. See [How to Search for Messages](../core/how-to-search-for-messages.md) for more information.

2.  Double-click the suspended message that you want to investigate to display the **Message Details** dialog box for the message.

3.  Click a message part in the left hand pane of the **Message Details** dialog box to display the message part.

    > [!NOTE]
    >  Messages may have 0, 1 or many message parts. Most often messages have single message part that is called "body".

4.  Click the **Binary** tab in the right hand pane of the **Message Details** dialog box to display the hexadecimal representation of the message part.

5.  Check the hexadecimal representation of characters in message parts for the following:

    -   Missing or invalid byte order mark. For more information about byte order marks see [http://go.microsoft.com/fwlink/?LinkId=196380](https://go.microsoft.com/fwlink/?LinkId=196380).

    -   Differences between the encoding of linebreaks in Unix and Windows. Unix uses hex linefeed (0A) to indicate a line break where Windows uses both hex carriage return (0D) and linefeed (0A) to indicate a line break.

    -   Invalid control character(s) in message parts. Control characters in message parts that do not show up in the text view may be visible in the binary view.

    -   Invalid nul character(s) in the middle of a message part can cause the message part to be truncated. The nul character is represented as hex (00).

    -   Invalid character offset in positional flat files. Display the hexadecimal representation of a message part to view the offset of data in a positional flat file.

## See Also
 [Investigating Orchestration, Port, and Message Failures](../core/investigating-orchestration-port-and-message-failures.md)