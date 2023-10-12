---
description: "Learn more about: Troubleshooting Host Initiated SSO"
title: "Troubleshooting Host Initiated SSO"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Troubleshooting Host Initiated SSO
The primary method of troubleshooting host initiated Single Sign-On (SSO) is tracing.

## Tracing
 Use the Trace command-line utility to enable tracing in SSO.

> [!NOTE]
>  For the trace command to function, the file tracelog.exe must be in the following directory:
>
>  \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.
>
>  You can download this file from the following location:
>
>  [https://go.microsoft.com/fwlink/?LinkId=33023](https://go.microsoft.com/fwlink/?LinkId=33023)

#### To use the trace utility

1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.

2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.

     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.

3.  Type `Trace –start –high` to set the tracing level to high and begin the trace.

4.  Run the scenario with host initiated SSO.

5.  Type `Trace –stop` to end the trace.

6.  A .bin file is generated in the directory above, which you can send to Microsoft for analysis.

## See Also
 [Host Initiated Single Sign-On](../esso/host-initiated-single-sign-on.md)
