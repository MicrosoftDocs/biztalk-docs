---
description: "Learn more about: How to Use the Trace Utility in Host Initiated SSO"
title: "How to Use the Trace Utility in Host Initiated SSO"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use the Trace Utility in Host Initiated SSO
The primary method of troubleshooting is tracing.

## Tracing
 Use the Trace command line utility to enable tracing in SSO.

> [!NOTE]
>  For the trace command to function, the file tracelog.exe must be in the following directory:
>
>  \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On

For more information on this tool, go to [Tracelog](/windows-hardware/drivers/devtest/tracelog).

#### To use the trace utility

1.  On the **Start** menu, click **Run**.

2.  In the **Run** dialog box, type **cmd**, and then click **OK**.

3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.

4.  Type **Trace –start –high** to set the tracing level to high and begin the trace.

5.  Run the scenario with host initiated SSO.

6.  Type **Trace –stop** to end the trace. A .bin file is generated in the directory above, which you can send to Microsoft for analysis.

## See Also
 [Host Initiated SSO](../core/host-initiated-sso.md)
