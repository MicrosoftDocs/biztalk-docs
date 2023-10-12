---
description: "Learn more about: How to Diagnose Problems with the HTTP Adapter"
title: "How to Diagnose Problems with the HTTP Adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Diagnose Problems with the HTTP Adapter
This section contains steps that can be followed to help diagnose problems with the HTTP adapter.

### Check the IIS and HTTPERR log files of the IIS Server for errors

- The source or target IIS server log files can contain information that is helpful for troubleshooting problems with the HTTP adapter. By default the IIS log files on a Windows Server are located in the following directory:

   <em>%WinDir%\\</em>system32\LogFiles\W3SVC1\

  > [!NOTE]
  >  *%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.

   By default the HTTPERR log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] based computer are located in the following directory:

   <em>%WinDir%\\</em>system32\LogFiles\HTTPERR\

  > [!NOTE]
  >  The HTTPERR log file is available only on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computers.

### Isolate problems with the HTTP send adapter by posting to the destination URL with a client that uses the System.Net.HttpWebRequest class

1.  If the HTTP send adapter is generating errors when posting to the destination URL, create a client that uses the System.Net.HttpWebRequest and HttpWebResponse classes to post to the destination URL. This approach will help determine if the problem is specific to the HTTP send adapter or if there is a problem posting to the destination URL in general.

2.  For more information about creating a client that uses the System.Net.HttpWebRequest and HttpWebResponse classes, go to [System.Net.Http: HttpClient Class](/dotnet/api/system.net.http.httpclient).

## See Also
 [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md)
 [Troubleshooting the HTTP Adapter](../core/troubleshooting-the-http-adapter.md)
